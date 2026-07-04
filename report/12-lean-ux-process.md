### 1.2.2. Lean UX Process

#### 1.2.2.1. Lean UX Problem Statement

El estado actual de la seguridad operacional en minería de tajo abierto se ha enfocado principalmente en mejorar la productividad y eficiencia del transporte mediante el uso de camiones autónomos de alto tonelaje, atendiendo a supervisores de centro de control junto a conductores de vehículos livianos que comparten rutas de acarreo, cuyo principal punto de dolor son las colisiones por puntos ciegos y la latencia de los sistemas GPS actuales.

Lo que los productos y servicios existentes no logran resolver es la falta de un sistema inteligente capaz de anticipar en tiempo real incursiones peligrosas de vehículos menores dentro de rutas autónomas críticas, permitiendo actuar preventivamente antes de que ocurra un accidente.

Nuestro producto abordará esta brecha mediante una red distribuida de sensores IoT y monitoreo en tiempo real, permitiendo detectar la proximidad de vehículos menores en zonas restringidas, generar alertas tempranas y fortalecer la seguridad operativa en entornos mineros automatizados.

Nuestro enfoque inicial será las empresas mineras de tajo abierto en Perú que operan flotas autónomas o semiautónomas con alto tránsito de vehículos auxiliares en rutas internas.

Sabremos que tuvimos éxito cuando observemos una reducción de riesgos e incidentes de colisión en rutas autónomas, una respuesta más rápida ante invasiones de ruta y una mejora en la percepción de seguridad por parte del personal operativo.

+ **Domain:** Seguridad industrial minera y monitoreo inteligente de transporte autónomo.

+ **Customer Segments:** Empresas operadoras mineras de tajo abierto y compañías de infraestructura vial industrial.

+ **Pain points:**
  + Riesgo de incursión de vehículos menores en rutas autónomas
  + Tiempo de reacción limitado de camiones de alto tonelaje
  + Accidentes de alto impacto económico y humano
  + Ausencia de alertas en tiempo real

+ **Gap:** No existe una solución accesible e integrada enfocada en detectar y alertar incursiones en rutas autónomas mineras mediante sensores IoT y monitoreo en tiempo real.

+ **Vision/Strategy:** Desarrollar una plataforma IoT con sensores distribuidos y dashboard centralizado que permita detectar invasiones de ruta, emitir alertas inmediatas y mejorar la seguridad operacional minera.

+ **Initial Segment:** Operaciones mineras en Perú que utilizan flotas autónomas o semiautónomas y presentan alto tránsito de vehículos auxiliares en rutas internas.


#### 1.2.2.2. Lean UX Assumptions

##### Business Assumptions

1. **Creemos que nuestros clientes tienen la necesidad** de prevenir colisiones entre vehículos livianos y camiones autónomos en tiempo real.

2. **Estas necesidades se pueden resolver** mediante una red de sensores IoT distribuidos con monitoreo continuo y alertas inmediatas de incursión.

3. **Nuestros clientes iniciales serán** empresas mineras de tajo abierto en Perú que operan flotas autónomas o semiautónomas. 

4. **El valor #1 que el cliente quiere obtener de nuestro servicio es** reducir riesgos de accidentes críticos y evitar pérdidas operativas y económicas. 

5. **El cliente también obtendrá beneficios adicionales:** visibilidad en tiempo real del estado de rutas, datos para análisis de seguridad y trazabilidad de incidentes para auditorías. 

6. **Adquiriremos la mayoría de nuestros clientes mediante** pruebas piloto (PoC) en campo, alianzas con distribuidores de maquinaria y presencia en ferias como PERUMIN.

7. **Generaremos ingresos mediante**  suscripción a la plataforma, implementación inicial del hardware IoT y servicios de mantenimiento/soporte.

8. **Nuestra competencia en el mercado serán** sistemas de monitoreo tradicionales, soluciones de geolocalización GPS y plataformas de seguridad industrial no especializadas en rutas autónomas. 

9. **Tendremos ventaja frente a la competencia por** nuestra capacidad de detección en tiempo real mediante IoT, integración Edge + Cloud y enfoque específico en incursiones de ruta. 

10. **El mayor riesgo del producto es** la precisión y confiabilidad de la detección de incursiones en condiciones reales de mina. 

11. **Resolveremos ese riesgo mediante** pruebas piloto, calibración de sensores y validación continua en condiciones simuladas y reales.

12. **Otro riesgo es** la resistencia de las mineras a adoptar nueva tecnología por costos o integración con sistemas existentes; lo mitigaremos con un modelo de PoC de bajo compromiso inicial.

##### User Assumptions

1. ¿Quién es el usuario? 

Supervisores de centro de control, operadores de despacho e ingenieros de seguridad; y conductores de vehículos livianos que circulan en rutas compartidas.

2. ¿Dónde encaja nuestro producto en su vida? 

El producto se integra directamente en las actividades de monitoreo, supervisión y gestión de seguridad en rutas de transporte minero. Se convierte en una herramienta clave dentro del centro de control y en campo, apoyando la toma de decisiones en tiempo real.

3. ¿Qué problemas resuelve nuestro producto? 

Resuelve la falta de visibilidad en tiempo real sobre incursiones en rutas autónomas, reduce el riesgo de colisiones críticas, mejora el tiempo de reacción ante eventos peligrosos y disminuye pérdidas económicas y riesgos humanos asociados a accidentes.

4. ¿Cuándo y cómo se usa nuestro producto? 

De forma continua y en segundo plano durante la operación; el supervisor interactúa vía dashboard y el conductor vía alertas en cabina.

5. ¿Qué características son importantes? 

Son importantes la detección en tiempo real, alta precisión de alertas, baja latencia, confiabilidad del sistema, visualización clara de eventos y facilidad de uso del dashboard.

6. ¿Cómo debería lucir y comportarse el producto?

Interfaz clara, profesional y de lectura rápida; comportamiento inmediato, preciso y confiable, priorizando la inmediatez de la notificación.

##### Feature Assumptions

+ Suponemos que el usuario necesita visualizar en tiempo real la ubicación de los eventos de incursión en rutas mineras.

+ Suponemos que el usuario necesita recibir alertas inmediatas cuando se detecte una invasión de ruta.

+ Suponemos que el usuario necesita diferenciar niveles de riesgo (bajo, medio, alto) según la proximidad o velocidad del vehículo.

+ Suponemos que el usuario necesita un historial de eventos para analizar incidentes y mejorar la seguridad.

+ Suponemos que el usuario necesita que el sistema debe activar alertas físicas (luces o sonido) en los vehículos autónomos o puntos de control.

+ Suponemos que el usuario necesita que el sistema debe funcionar de manera continua y automática sin intervención constante del usuario.

#### 1.2.2.3. Lean UX Hypothesis

Creemos que lograremos reducir el tiempo de detección de incursiones en ruta
si los supervisores de centro de control alcanzan una visibilidad inmediata y centralizada de las zonas de riesgo con un dashboard de monitoreo en tiempo real con mapa de zonas y estado operativo.

Creemos que lograremos disminuir la cantidad de "casi accidentes" por invasión de ruta
si los conductores de vehículos livianos alcanzan una advertencia oportuna antes de ingresar a una zona restringida con alertas automáticas de proximidad emitidas en cabina por el nodo IoT.

Creemos que lograremos mejorar la priorización de la respuesta operativa y evitar la sobrecarga de alertas si los supervisores de centro de control
alcanzan la capacidad de atender primero los eventos más críticos con un motor que clasifica las alertas por nivel de riesgo (bajo, medio, crítico) según distancia, velocidad y trayectoria.

Creemos que lograremos fortalecer la cultura de seguridad y soportar auditorías
si los supervisores e ingenieros de seguridad
alcanzan la capacidad de analizar incidentes y patrones de riesgo recurrentes
con un historial consultable y reportes exportables de eventos y alertas.

Creemos que lograremos incrementar la capacidad de reacción ante un riesgo inminente
si los conductores de vehículos livianos
alcanzan una percepción inmediata e inequívoca del peligro sin distraerse de la conducción
con alertas visuales (LED RGB) y sonoras (buzzer) activadas localmente por el dispositivo de cabina.

Creemos que lograremos reducir el tiempo de comunicación de una emergencia al centro de control
si los conductores de vehículos livianos alcanzan la posibilidad de reportar un peligro inmediato sin depender de la radio con un botón de pánico físico que publica una alerta crítica prioritaria con geolocalización.

Creemos que lograremos prevenir accidentes asociados al factor humano
si los conductores de vehículos livianos
alcanzan una alerta temprana cuando presentan signos de fatiga
con el monitoreo continuo del ritmo cardíaco mediante el sensor de pulso.

#### 1.2.2.4. Lean UX Canvas

 <img src="assets/lean_ux_canvas.png" alt="leanuxcanvas">
