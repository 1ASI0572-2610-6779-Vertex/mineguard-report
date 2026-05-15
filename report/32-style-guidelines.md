## Capítulo V: Solution UI/UX Design

### 5.1. Style Guidelines

La sección de Style Guidelines establece los lineamientos visuales y de diseño que garantizan una experiencia de usuario coherente, clara y alineada con la identidad de marca de MineGuard. Este repositorio central reúne todos los elementos gráficos y normativos necesarios para que el equipo de diseño y desarrollo trabaje de manera consistente en los distintos canales digitales (web, móvil e IoT) del sistema de mitigación de colisiones para carros mineros.

Su objetivo principal es mantener una presentación uniforme y profesional, fortaleciendo la identidad visual de la solución y asegurando que cada interacción transmita confianza, seguridad operacional y precisión técnica, aspectos críticos en entornos de minería de alto riesgo.

Para lograr este objetivo esta sección se dividirá en dos sub-secciones:

* General Style Guidelines: Se definirán los principios básicos de diseño incluyendo branding, tipografía, paleta de colores, espaciado y tono comunicacional.
* Web, Mobile and IoT Style Guidelines: Aquí se definen los estándares visuales específicos para cada plataforma.

Estos lineamientos permiten mantener organizados y accesibles todos los artefactos de diseño, reduciendo inconsistencias y mejorando la eficiencia del equipo.

#### 5.1.1. General Style Guidelines

Los lineamientos generales de estilo definen los principios transversales de diseño que guiarán la identidad visual de MineGuard en todas sus plataformas digitales. Incluyen decisiones clave en torno al branding, paleta de colores, tipografía, tono comunicacional y principios de diseño.

**Branding:**

El logotipo se empleará principalmente en su versión sobre fondos oscuros, alineada con la naturaleza industrial del producto y los entornos operativos donde se utilizará (salas de control, cabinas de equipo pesado, dispositivos de monitoreo). Se debe mantener un área de seguridad alrededor del logotipo equivalente a la altura de la letra "M" de MineGuard para garantizar su visibilidad.

* El logo completo se utilizará en la barra de navegación superior de la plataforma web y en las pantallas principales de la aplicación móvil.
* El isotipo se aplicará únicamente en espacios reducidos, como íconos de aplicaciones móviles, pestañas del navegador, indicadores en dispositivos IoT y favicons.

_Logo:_

![logo](./report/assets/mineguard-logo-final.png)

_Isotipo:_

![isotipo](./report/assets/mineguard-logo-final-2.png)

**Paleta de colores:**

La identidad visual se basa en una combinación de azul, amarillo y tonos oscuros, diseñados para transmitir tecnología, alerta y seguridad operacional, atributos esenciales en la industria minera.

* Colores principales: el azul `#2876E9` refuerza la percepción de tecnología, precisión y confiabilidad; el amarillo `#ECB014` se inspira en los estándares de alta visibilidad (Hi-Vis) propios de la minería y se reserva para acentos, alertas y elementos críticos.
* Fondos y textos: el negro `#131313` se utiliza como fondo principal para reducir fatiga visual en pantallas de monitoreo continuo, mientras que el blanco `#FFFFFF` se aplica en tipografía principal e íconos sobre fondo oscuro, asegurando alta legibilidad.
* Colores secundarios: tonos derivados del azul y del amarillo se reservan para estados de hover, indicadores de estado (operativo, advertencia, crítico) y llamadas a la acción.

![color palette](./report/assets/paleta-de-colores.png)

**Tipografía:**

La tipografía principal será Poppins, elegida por su carácter geométrico, su excelente legibilidad en pantallas y su afinidad visual con el logotipo de MineGuard.

* Se aplicarán jerarquías tipográficas claras, diferenciando títulos, subtítulos y cuerpo de texto.
* Se hará uso de la variante Bold 700 para destacar información crítica, alertas y métricas operativas clave.
* La variante Regular 400 se reserva para texto descriptivo, etiquetas y contenido secundario.

![typography](./report/assets/mineguard-tipografia.png)

**Tono y lenguaje:**

La comunicación seguirá un tono profesional, técnico y directo, adecuado a un entorno industrial de alta exigencia operativa.

* Se priorizará la claridad, la precisión y la brevedad en los textos, especialmente en alertas y notificaciones.
* El estilo de comunicación debe transmitir confianza, control y orientación a la seguridad.
* Se evitarán ambigüedades en mensajes críticos: las alertas deben indicar de forma inequívoca el evento, su severidad y la acción recomendada.

**Principios de diseño:**

El diseño se regirá por los siguientes principios:

* Consistencia: mantener coherencia visual en todos los elementos y plataformas.
* Claridad: privilegiar la legibilidad de información crítica por encima de la ornamentación.
* Seguridad visual: las alertas y estados críticos deben ser inequívocos, aprovechando el contraste de color y la jerarquía tipográfica.
* Accesibilidad: garantizar contrastes adecuados y tamaños tipográficos legibles en condiciones de iluminación variable (cabinas, exteriores, salas oscuras).
* Espaciado adecuado: entre elementos para mejorar la lectura rápida en situaciones de monitoreo continuo.
* Iconografía clara: símbolos simples, reconocibles y consistentes con convenciones de la industria minera.
* Uso de contrastes: para resaltar información crítica y facilitar la navegación bajo presión operativa.

#### 5.1.2. Web, Mobile and IoT Style Guidelines

Esta sección establece los estándares visuales e interactivos para los distintos canales digitales de MineGuard: interfaz web de supervisión, aplicación móvil para operadores y supervisores en campo, y dispositivos IoT instalados en los carros mineros. Cada uno presenta particularidades de interacción y diseño, pero todos comparten la misma identidad visual definida en los lineamientos generales.

**Web Style Guide:**

Componentes:

* Botones: se definen estilos primario (azul `#2876E9`), secundario (contorno blanco) y de alerta (amarillo `#ECB014` para acciones críticas), con diferencias claras en color y contraste.
* Formularios: incluyen campos de texto sobre fondo oscuro, validaciones visuales y selectores uniformes.
* Cards: tarjetas utilizadas para mostrar el estado de cada carro minero, alertas activas y métricas resumidas, con variantes para destacar eventos críticos.
* Tablas: estilo simple con uso de bordes internos y jerarquía tipográfica para cabeceras, optimizadas para listados de eventos, vehículos y reportes.
* Mapa operacional: vista central del dashboard que muestra la posición y estado en tiempo real de los carros mineros dentro de la operación.

Comportamiento de componentes:

* Estados de interacción (hover, active, focus) se aplican de manera sutil, priorizando que la atención del usuario permanezca en la información operativa.
* Las alertas críticas se distinguen mediante combinación de color (amarillo) y refuerzo tipográfico (Bold 700) para garantizar lectura inmediata.

Responsive design:

* Interfaz diseñada principalmente para desktop y pantallas grandes de sala de control, con adaptación proporcional según el tamaño de la ventana.
* Se prioriza la legibilidad y la correcta distribución del contenido en resoluciones amplias propias de entornos de monitoreo.

Íconos e ilustraciones:

* No se utilizarán ilustraciones a color.
* Los íconos serán siluetas simples (en blanco sobre fondo oscuro) y su presencia se limitará a indicadores funcionales y de estado.

**Mobile Style Guide:**

Componentes:

* Botones: variantes primary (azul) y secondary (contorno), con áreas táctiles amplias adecuadas para uso con guantes en campo.
* Formularios: campos de texto optimizados para teclado móvil, validaciones claras y selectores de fácil interacción.
* Cards: diseño compacto para mostrar el estado del vehículo, alertas recientes y métricas clave de manera jerárquica y accesible.
* Indicadores de estado: chips de color (verde / amarillo / rojo sobre la paleta base) para comunicar rápidamente la condición operacional del equipo.

Gestos:

* Tap: gesto principal para interacción con botones y elementos táctiles.
* Swipe vertical: navegación entre pantallas o listas de eventos.
* Swipe horizontal: navegación entre vistas de monitoreo o descarte rápido de notificaciones no críticas.
* Long press: acceso a acciones secundarias sobre un vehículo o alerta.

Responsive Design:

* Adaptación automática a resoluciones de smartphones y tablets robustas usadas en campo.
* Se prioriza la usabilidad en pantallas medianas con tipografía legible y áreas táctiles amplias para interacción con guantes o en condiciones de movimiento.

**IoT Style Guide:**

Dispositivos integrados en los carros mineros y unidades de alerta auxiliares:

* Indicadores visuales: uso de LED con la paleta de la marca (azul para estado operativo, amarillo para advertencia, rojo derivado para evento crítico).
* Pantallas embarcadas: cuando aplique, mantienen la tipografía Poppins en variante Bold con tamaños amplios para lectura rápida desde la cabina.
* Jerarquía de alertas: la información crítica siempre ocupa la zona central de la pantalla y se acompaña de refuerzo sonoro definido por el sistema.
* Contraste: se garantiza contraste alto entre texto e iconografía sobre fondo oscuro para asegurar visibilidad en condiciones de polvo, vibración e iluminación variable propias de la operación minera.
