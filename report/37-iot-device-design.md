# 5.6. IoT Device Design

## Introducción

La propuesta de diseño de los dispositivos IoT de Mineguard se fundamenta en tres criterios principales: detección anticipada de riesgos en rutas de transporte autónomo, monitoreo continuo del estado fisiológico del conductor de vehículos livianos, y comunicación de baja latencia con el centro de control mediante el protocolo MQTT. Los dispositivos actúan como la primera capa de captura de datos del entorno operativo minero, complementando el dashboard de supervisión con información objetiva sin depender de la observación humana, factor identificado como el principal punto vulnerable en las entrevistas realizadas (66.7% de los expertos consultados).

Ambos dispositivos se construyen sobre el microcontrolador ESP32 DevKit V1, que ofrece conectividad Wi-Fi integrada, procesamiento dual-core suficiente para el firmware embebido en C++ y un amplio ecosistema de bibliotecas open-source. La comunicación con el backend se realiza mediante el protocolo MQTT 3.1.1 sobre TLS 1.2, publicando eventos al broker AWS IoT Core, donde los microservicios de los Bounded Contexts *Service Execution and Monitoring* y *Dashboard and Analytics* los consumen y actualizan el estado del sistema en tiempo real.

| Decisión técnica | Valor |
|---|---|
| Microcontrolador | ESP32 DevKit V1 (30 pines) |
| Protocolo de comunicación | MQTT 3.1.1 sobre TLS 1.2 |
| Broker | AWS IoT Core |
| Calidad de servicio | QoS 1 (entrega garantizada) |
| Autenticación | Certificados X.509 por dispositivo |
| Firmware | C++ (framework Arduino) |
| Simulador | Wokwi |

---

## Aplicación del Framework IoT System Design Steps

Para fundamentar la selección de los dispositivos y componentes, se aplicó el framework de **IoT System Design Steps** de 12 pasos, garantizando que cada decisión técnica responda a un requisito concreto del sistema y no a una preferencia arbitraria.

### Paso 1: Definición de los requisitos del sistema

A partir del análisis de entrevistas, user personas y user stories documentadas en capítulos previos, se identificaron los siguientes requisitos funcionales:

- **RF-01**: Detectar la proximidad entre vehículos livianos y zonas de tránsito autónomo restringido (US01–US06).
- **RF-02**: Monitorear el ritmo cardíaco del conductor para identificar signos de fatiga (US07).
- **RF-03**: Emitir alertas sonoras y visuales en cabina cuando se detecta riesgo (US07, US08).
- **RF-04**: Permitir al conductor activar manualmente una alerta de pánico (US43).
- **RF-05**: Reportar la geolocalización de los vehículos en tiempo real al centro de control.
- **RF-06**: Detectar y notificar fallos de comunicación de los nodos sensores (US46 — Watchdog).

Adicionalmente, se identificaron requisitos no funcionales críticos: latencia de alerta menor a 500 ms, autonomía mínima de 8 horas para el dispositivo wearable, y resistencia al polvo y vibración propios del entorno minero.

### Paso 2: Selección de la tipología del sistema IoT

Se optó por una arquitectura distribuida de nodos heterogéneos con dos tipologías de dispositivo:

1. **Nodo móvil (wearable de cabina)**: alimentado por batería, asociado a cada conductor, con sensores fisiológicos y elementos de interacción directa.
2. **Nodo fijo (proximidad en ruta)**: instalado en puntos críticos de la ruta minera (cruces, accesos a zonas autónomas), alimentado por la red eléctrica del sitio, con sensores de proximidad y geolocalización.

Ambos nodos publican eventos a un broker central en la nube (AWS IoT Core), que actúa como intermediario hacia los microservicios del backend y el dashboard web del supervisor.

### Paso 3: Definición de los requisitos de la capa física

El entorno minero impone restricciones específicas a la capa física:

| Requisito | Especificación |
|---|---|
| Rango de temperatura operativa | –10 °C a +60 °C |
| Resistencia mecánica | Vibración continua, golpes esporádicos |
| Conectividad inalámbrica | Wi-Fi 2.4 GHz (cobertura del sitio minero) |
| Alimentación nodo móvil | Batería Li-Ion 18650 (3.7 V, ≥ 2200 mAh) |
| Alimentación nodo fijo | Red eléctrica 5 V DC vía adaptador |
| Protección | Carcasa IP54 mínima (polvo y salpicaduras) |

### Paso 4: Definición de los requisitos de la capa de intercambio

La capa de intercambio implementa MQTT sobre Wi-Fi con las siguientes garantías:

- **Protocolo**: MQTT 3.1.1 sobre TLS 1.2 (no se admite tráfico en texto plano).
- **QoS**: nivel 1 — el broker confirma la recepción de cada mensaje crítico.
- **Mecanismo de keep-alive**: 30 segundos. Si un nodo no responde, se dispara el Watchdog del US46.
- **Topics jerárquicos**:
  - `mineguard/driver/{driverId}/heartrate`
  - `mineguard/driver/{driverId}/panic`
  - `mineguard/zone/{zoneId}/proximity`
  - `mineguard/zone/{zoneId}/gps`
  - `mineguard/zone/{zoneId}/status`

### Paso 5: Definición de los requisitos de la capa de información

Los payloads se serializan en formato **JSON UTF-8** con un esquema común por tipo de evento. Ejemplo del nodo móvil:

```json
{
  "driverId": "D-1023",
  "timestamp": "2026-05-15T14:30:22Z",
  "heartRate": 112,
  "fatigueLevel": "MEDIUM",
  "deviceBattery": 78
}
```

Ejemplo del nodo fijo:

```json
{
  "zoneId": "Z-A07",
  "timestamp": "2026-05-15T14:30:25Z",
  "distance_m": 4.2,
  "gps": { "lat": -16.4090, "lon": -71.5375 },
  "alertLevel": "HIGH"
}
```

### Paso 6: Definición de los requisitos de la capa de servicios de aplicación

Los dispositivos se integran con los siguientes Bounded Contexts definidos en el capítulo 4:

| Bounded Context | Función respecto al IoT |
|---|---|
| Service Execution and Monitoring | Recibe telemetría en tiempo real, detecta condiciones de riesgo y dispara alertas |
| Dashboard and Analytics | Agrega y visualiza datos históricos y en vivo para el supervisor |
| Resource and Asset Management | Mantiene el registro de dispositivos, conductores y zonas asociadas |
| Profiles and Preferences Management | Asocia umbrales personalizados de fatiga por conductor |

### Paso 7: Selección de las arquitecturas de intercambio e integración

- **Broker**: AWS IoT Core con autenticación mutua mediante certificados X.509.
- **Bridge a backend**: AWS IoT Rules → AWS Lambda → API REST de los microservicios.
- **Dashboard en tiempo real**: suscripción WebSocket sobre los topics MQTT relevantes.
- **Persistencia**: AWS Timestream para series temporales (telemetría) y PostgreSQL para entidades de dominio.

### Paso 8: Selección de sensores y actuadores

La selección de cada componente responde a un requisito funcional específico:

| Componente | Tipo | Requisito atendido | Justificación |
|---|---|---|---|
| HC-SR04 | Sensor ultrasónico | RF-01 | Mide distancia 2 cm–4 m con precisión ±3 mm, ideal para zonas restringidas |
| Sensor de pulso SP-203 | Sensor fotoeléctrico | RF-02 | Detecta variaciones de pulso asociadas a fatiga y somnolencia |
| GPS NEO-6M | Receptor GNSS | RF-05 | Precisión 2.5 m, suficiente para ubicar nodos en mapa minero |
| Buzzer activo 5V | Actuador sonoro | RF-03 | Alerta audible en cabina por encima del ruido del motor |
| WS2812B (LED RGB) | Actuador visual | RF-03 | Cambio de color por estado, retroalimentación inmediata |
| LCD 20×4 I2C | Display | RF-03 | Muestra mensajes legibles bajo luz solar directa |
| Push button (rojo) | Entrada usuario | RF-04 | Activación manual de alerta de pánico |

### Paso 9: Selección del microcontrolador y transceivers de radio

Se evaluaron tres alternativas: **Arduino UNO + ESP8266**, **ESP32 DevKit V1** y **Raspberry Pi Pico W**. La decisión recayó en el **ESP32 DevKit V1** por los siguientes motivos:

| Criterio | ESP32 DevKit V1 | Justificación |
|---|---|---|
| Procesamiento | Xtensa LX6 dual-core @ 240 MHz | Suficiente para algoritmos de filtrado de señal de pulso y procesamiento de tramas NMEA del GPS en paralelo |
| Conectividad | Wi-Fi 2.4 GHz + BLE 4.2 integrados | Elimina la necesidad de módulos externos; reduce costo y complejidad |
| GPIOs | 30 pines (24 utilizables) | Cobertura holgada para los 6–7 componentes por dispositivo |
| Consumo | Modo deep-sleep: 10 µA | Permite cumplir la autonomía mínima de 8 horas con batería 18650 |
| Compatibilidad firmware | Framework Arduino C++ | Reusa el ecosistema visto en clase y bibliotecas open-source maduras |
| Costo unitario | ~S/ 25 | Competitivo para producción a escala piloto |
| Simulador | Soportado nativamente por Wokwi | Permite validar el prototipo antes del despliegue físico |

### Paso 10: Definición del procesamiento de datos por nodo y en la nube

**Procesamiento en el borde (Edge — ESP32):**
- Filtrado de outliers en las lecturas de pulso (media móvil de 5 muestras).
- Cálculo de BPM a partir de la señal cruda del SP-203.
- Filtrado de ecos espurios en el HC-SR04 (descarta lecturas mayores a 400 cm).
- Parseo de tramas NMEA del GPS NEO-6M.
- Aplicación de umbrales locales antes de publicar (no publica si no hay cambio significativo).

**Procesamiento en la nube (AWS):**
- Correlación cruzada entre nodos próximos para confirmar incidentes.
- Agregación de telemetría por turno y por conductor.
- Activación de reglas de negocio (envío de SMS al supervisor en alertas críticas).
- Persistencia y analytics histórico.

### Paso 11: Análisis del tiempo de procesamiento

Los tiempos de procesamiento se definieron considerando la criticidad de cada flujo:

| Etapa | Latencia objetivo | Latencia esperada |
|---|---|---|
| Lectura de sensor (HC-SR04) | < 50 ms | ~30 ms |
| Procesamiento local en ESP32 | < 100 ms | ~50 ms |
| Publicación MQTT al broker | < 200 ms | ~120 ms |
| Procesamiento en cloud + dashboard | < 150 ms | ~100 ms |
| **Total: sensor → alerta visible** | **< 500 ms** | **~300 ms** |

### Paso 12: Definición de la interfaz gráfica de usuario

La interacción con el usuario se distribuye entre tres superficies:

1. **Dispositivo del conductor**: LCD 20×4 con mensajes textuales (estado, alertas, instrucciones) + LED RGB de estado + buzzer.
2. **Nodo fijo de ruta**: LED RGB visible a distancia + buzzer externo (no requiere display porque no hay operador en sitio).
3. **Dashboard web del supervisor**: vista en tiempo real con mapa de calor, lista de alertas activas, estado de cada dispositivo y métricas históricas.

---

## Dispositivo 01: Wearable del Conductor (Driver Safety Wearable)

### Descripción y criterios de diseño

El Driver Safety Wearable monitorea continuamente el estado fisiológico del conductor del vehículo liviano y le proporciona un canal directo de alerta hacia el centro de control. El dispositivo se instala en el tablero del vehículo y se conecta al conductor mediante un clip auricular o pinza dactilar que captura la señal del sensor de pulso SP-203.

Cuando el sensor detecta variaciones en el ritmo cardíaco asociadas a somnolencia (descenso sostenido de BPM bajo el umbral configurado en el perfil del conductor), el ESP32 procesa la señal localmente, activa el buzzer y el LED RGB en color rojo, muestra el mensaje de alerta en el LCD 20×4 y publica el evento al tópico `mineguard/driver/{driverId}/heartrate`. Paralelamente, el botón rojo de pánico permite al conductor reportar manualmente una emergencia, publicando un evento al tópico `mineguard/driver/{driverId}/panic` con prioridad máxima.

El diseño físico sigue la guía de estilos IoT de Mineguard: carcasa compacta de ABS reforzado en color naranja de seguridad (alta visibilidad), con el LED RGB visible en la parte superior, el LCD en la cara frontal, el botón de pánico protegido por un anillo plástico para evitar activaciones accidentales, y carga mediante USB-C a través del módulo TP4056 integrado.

### Componentes

| Componente | Función |
|---|---|
| ESP32 DevKit V1 (30 pines) | MCU principal — Wi-Fi, MQTT, lógica de procesamiento de señal |
| Sensor de pulso SP-203 | Captura la señal fotoeléctrica del ritmo cardíaco |
| LCD 20×4 con interfaz I2C (PCF8574) | Display de mensajes y estado al conductor |
| Buzzer activo 5V | Alerta sonora audible en cabina |
| WS2812B (LED RGB) | Indicador visual de estado y nivel de alerta |
| Botón pulsador rojo | Activación manual de alerta de pánico |
| Batería Li-Ion 18650 (3.7 V, 2200 mAh) | Fuente de energía recargable portátil |
| Porta batería 18650 | Soporte y contactos para la celda |
| Módulo TP4056 (USB-C) | Carga y protección de batería Li-Ion |
| Resistencias 220 Ω / 330 Ω | Limitación de corriente para LEDs y entradas digitales |

### Simulación en Wokwi

 En Wokwi, el sensor SP-203 se reemplaza por un potenciómetro analógico conectado a GPIO34. El valor del potenciómetro (0–4095) se mapea linealmente al rango de BPM esperado (40–180). En hardware real, se reemplaza la función `analogRead(34)` por la lectura del SP-203 mediante el algoritmo de detección de picos cardíacos. El botón rojo y el resto de componentes funcionan idénticamente en simulación y en hardware.
 
La siguiente figura muestra el circuito del Driver Safety Wearable simulado en Wokwi, compuesto por el ESP32 DevKit V1, el potenciómetro (SP-203), la pantalla LCD 20×4 I2C, el buzzer activo, el LED NeoPixel WS2812B y el botón de pánico.
 
![Simulación Wokwi – Driver Safety Wearable](assets\driver-safety-warable.png)

### Flujo de interacción

1. El sensor SP-203 captura la señal fotoeléctrica del pulso del conductor de forma continua.
2. El ESP32 muestrea la señal a 100 Hz en GPIO34, aplica un filtro de media móvil de 5 muestras y calcula los BPM mediante detección de picos.
3. Si los BPM se mantienen fuera del rango normal (configurado en el perfil del conductor) durante más de 8 segundos consecutivos, se considera **fatiga detectada**.
4. Al detectar fatiga, el ESP32:
   - Activa el buzzer con un patrón intermitente (500 ms ON / 500 ms OFF).
   - Cambia el WS2812B a color rojo (#E24B4A).
   - Muestra en el LCD: `ALERTA: FATIGA` / `DETENGASE Y DESCANSE`.
   - Publica el payload JSON al tópico `mineguard/driver/{driverId}/heartrate` con `fatigueLevel: "HIGH"`.
5. Si el conductor presiona el botón rojo de pánico (GPIO15), independientemente del estado de pulso, el ESP32 publica inmediatamente al tópico `mineguard/driver/{driverId}/panic` con `priority: "CRITICAL"`, parpadea el LED en rojo y emite un patrón sonoro continuo.
6. Cada 30 segundos, el dispositivo publica un mensaje de heartbeat al tópico `mineguard/driver/{driverId}/status` para que el sistema de Watchdog (US46) confirme su disponibilidad.

### Tabla de conexiones (Pinout)

| Componente | Pin componente | Pin ESP32 | Tipo de señal |
|---|---|---|---|
| SP-203 (Pulso) | VCC | 3.3V | Alimentación |
| SP-203 (Pulso) | GND | GND | Referencia de tierra |
| SP-203 (Pulso) | SIG (Analog Out) | GPIO34 | ADC (0–3.3 V) |
| LCD 20×4 I2C | SDA | GPIO21 | I2C Data (400 kHz) |
| LCD 20×4 I2C | SCL | GPIO22 | I2C Clock (400 kHz) |
| LCD 20×4 I2C | VCC | 5V | Alimentación 5 V |
| LCD 20×4 I2C | GND | GND | Tierra |
| Buzzer activo | (+) | GPIO25 | PWM digital |
| Buzzer activo | (–) | GND | Tierra |
| WS2812B LED | DIN | GPIO5 | Datos serie (800 kbps) |
| WS2812B LED | VDD | 5V | Alimentación 5 V |
| WS2812B LED | GND | GND | Tierra |
| Botón pánico | Terminal 1 | GPIO15 | Entrada digital (pull-up interno) |
| Botón pánico | Terminal 2 | GND | Tierra |
| TP4056 (Batería) | OUT+ | VIN | Alimentación batería 3.7 V |
| TP4056 (Batería) | OUT– | GND | Tierra |

---

## Dispositivo 02: Nodo Fijo de Ruta Minera (Mining Route Proximity Node)

### Descripción y criterios de diseño

El **Mining Route Proximity Node** se instala en puntos críticos de la ruta minera —principalmente en los accesos a zonas de tránsito autónomo restringido, cruces de caminos y curvas de baja visibilidad— y actúa como guardián electrónico de la zona. Detecta cuando un vehículo (autónomo o liviano) se aproxima al rango de peligro mediante el sensor ultrasónico HC-SR04 y reporta su geolocalización exacta mediante el módulo GPS NEO-6M.

A diferencia del wearable, este nodo no requiere interacción humana: se alimenta de la red eléctrica del sitio (5 V DC mediante adaptador) y comunica los eventos al broker MQTT de forma totalmente autónoma. Cuando se detecta proximidad bajo el umbral crítico, el nodo activa simultáneamente su buzzer externo y su LED RGB en rojo para advertir visualmente a cualquier vehículo en aproximación, y publica el evento al tópico `mineguard/zone/{zoneId}/proximity`. El centro de control correlaciona esta información con la telemetría de los vehículos autónomos para emitir alertas preventivas.

El diseño físico considera la exposición al entorno minero: carcasa IP54 en color naranja de seguridad, soporte de montaje en poste o pared, y orientación del sensor HC-SR04 paralela a la dirección del tráfico.

### Componentes

| Componente | Función |
|---|---|
| ESP32 DevKit V1 (30 pines) | MCU principal — Wi-Fi, MQTT, lógica de procesamiento |
| Sensor HC-SR04 (Ultrasónico) | Mide la distancia hacia vehículos en aproximación (2 cm – 4 m) |
| Módulo GPS NEO-6M con antena (HW-248) | Reporta la geolocalización del nodo |
| Buzzer activo 5V | Alerta sonora externa para vehículos |
| WS2812B (LED RGB) | Señal visual de estado de la zona |
| Adaptador 5V USB-C | Alimentación desde red eléctrica del sitio |
| Resistencias 220 Ω | Limitación de corriente |

### Simulación en Wokwi

En Wokwi, el sensor HC-SR04 funciona de forma nativa: se puede arrastrar el objeto naranja frente al sensor para variar la distancia simulada en tiempo real. El módulo GPS NEO-6M no está disponible en Wokwi como componente nativo, por lo que se simula mediante un bloque de coordenadas fijas declaradas en el firmware. En hardware real, las coordenadas se leen del módulo NEO-6M mediante UART2 (GPIO16/17) parseando las tramas NMEA `$GPGGA`.
 
La siguiente figura muestra el circuito del **Mining Route Proximity Node** simulado en Wokwi, compuesto por el ESP32 DevKit V1, el sensor ultrasónico HC-SR04, el buzzer activo y el LED NeoPixel WS2812B.
 
![Simulación Wokwi – Mining Route Proximity Node](assets\Mining-route-proximity-node.png)


### Flujo de interacción

1. El sensor HC-SR04 emite un pulso ultrasónico cada 100 ms y mide el tiempo de retorno del eco.
2. El ESP32 convierte el tiempo en distancia mediante la fórmula `distancia_cm = (tiempo_us × 0.0343) / 2`.
3. Si la distancia medida cae bajo el umbral configurado (por defecto **300 cm**) y se mantiene durante al menos 2 lecturas consecutivas:
   - El nodo activa el buzzer en patrón rápido (200 ms ON / 200 ms OFF).
   - El WS2812B cambia a color **rojo (#E24B4A)** y comienza a parpadear.
   - Se publica el evento al tópico `mineguard/zone/{zoneId}/proximity` con `alertLevel: "HIGH"`.
4. Si la distancia se encuentra entre 300 cm y 500 cm, el LED se mantiene en **ámbar (#EF9F27)** indicando precaución, pero no se activa el buzzer.
5. Cuando la zona vuelve a estar libre (distancia > 500 cm durante 5 segundos), el LED retorna a **verde (#1D9E75)** y se publica el evento de zona despejada.
6. Cada 60 segundos, el nodo publica su geolocalización (`mineguard/zone/{zoneId}/gps`) y un heartbeat de estado para el sistema de Watchdog.

### Tabla de conexiones (Pinout)

| Componente | Pin componente | Pin ESP32 | Tipo de señal |
|---|---|---|---|
| HC-SR04 | VCC | 5V | Alimentación 5 V |
| HC-SR04 | GND | GND | Tierra |
| HC-SR04 | TRIG | GPIO5 | Salida digital (pulso 10 µs) |
| HC-SR04 | ECHO | GPIO18 | Entrada digital (eco) |
| GPS NEO-6M | VCC | 3.3V | Alimentación |
| GPS NEO-6M | GND | GND | Tierra |
| GPS NEO-6M | TX | GPIO16 (RX2) | UART2 RX (9600 baud) |
| GPS NEO-6M | RX | GPIO17 (TX2) | UART2 TX (9600 baud) |
| Buzzer activo | (+) | GPIO25 | PWM digital |
| Buzzer activo | (–) | GND | Tierra |
| WS2812B LED | DIN | GPIO4 | Datos serie (800 kbps) |
| WS2812B LED | VDD | 5V | Alimentación 5 V |
| WS2812B LED | GND | GND | Tierra |
| Adaptador 5V | VCC | VIN | Alimentación principal |
| Adaptador 5V | GND | GND | Tierra |

---

## Arquitectura de comunicación MQTT

Los dispositivos se comunican con el backend a través del protocolo **MQTT 3.1.1 sobre TLS 1.2**, publicando mensajes al broker **AWS IoT Core**. Los microservicios de los Bounded Contexts *Service Execution and Monitoring* y *Dashboard and Analytics* se suscriben a los tópicos correspondientes y actualizan el estado del sistema en tiempo real.

| Dispositivo | Tópico MQTT | Microservicio suscriptor |
|---|---|---|
| Driver Safety Wearable | `mineguard/driver/{driverId}/heartrate` | Monitoring Service (Service Execution BC) |
| Driver Safety Wearable | `mineguard/driver/{driverId}/panic` | Alert Service (Service Execution BC) |
| Driver Safety Wearable | `mineguard/driver/{driverId}/status` | Watchdog Service (Service Execution BC) |
| Mining Route Proximity Node | `mineguard/zone/{zoneId}/proximity` | Risk Assessment Service (Service Execution BC) |
| Mining Route Proximity Node | `mineguard/zone/{zoneId}/gps` | Asset Tracking Service (Resource and Asset Management BC) |
| Mining Route Proximity Node | `mineguard/zone/{zoneId}/status` | Watchdog Service (Service Execution BC) |

La **autenticación** con AWS IoT Core se realiza mediante certificados X.509 emitidos por dispositivo durante el proceso de provisioning. Cada nodo posee un identificador único (`driverId` o `zoneId`) que se asocia a su certificado y permite la trazabilidad completa de los eventos.

---

## Paleta de colores LED — Guía de estilos IoT Mineguard

La paleta de colores del LED RGB de ambos dispositivos sigue la guía de estilos IoT del producto, alineada con la semántica de seguridad estándar en entornos industriales:

| Color | Hex | Condición |
|---|---|---|
|  Verde | `#1D9E75` | Zona segura / estado normal / pulso del conductor en rango |
|  Ámbar | `#EF9F27` | Proximidad media (300–500 cm) / fatiga incipiente |
|  Rojo | `#E24B4A` | Alerta crítica: proximidad < 300 cm, fatiga confirmada o pánico activo |
|  Azul | `#378ADD` | Dispositivo conectando o sincronizando con el broker |
|  Blanco | `#F5F5F5` | Modo de configuración / mantenimiento |
|  Gris | `#888780` | Dispositivo en standby / sin actividad |

Esta semántica cromática es consistente con la guía de estilos definida para las interfaces gráficas del dashboard del supervisor y la aplicación móvil del conductor, garantizando una experiencia unificada entre el mundo físico y el digital.