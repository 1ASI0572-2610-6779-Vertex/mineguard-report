## 6.3. Validation Interviews.
### 6.3.1. Diseño de Entrevistas.

Para esta etapa del proyecto se diseñaron entrevistas de validación orientadas a comprobar si los usuarios de los segmentos objetivo comprenden la propuesta de valor de MineGuard, identifican correctamente los beneficios del sistema y pueden interactuar de manera clara con los artefactos digitales desarrollados: Landing Page y Web Application. A diferencia de las entrevistas exploratorias realizadas al inicio del proyecto, estas tienen como propósito validar la experiencia del usuario frente a una solución ya implementada. Por ello, los participantes no solo responderán preguntas, sino que también interactuarán con el Landing Page y la aplicación web.

+ Segmento 1: Supervisión Corporativa en Minería de Tajo Abierto

    Este segmento está conformado por supervisores de centro de control, operadores de despacho, jefes de operaciones y responsables de seguridad minera. Para este grupo, la validación se enfoca en comprobar si MineGuard permite comprender rápidamente el estado de la operación, interpretar alertas críticas y apoyar la toma de decisiones frente a riesgos de colisión.

    | Elemento a validar    | Descripción                                                                                                                                                                                       |
    | --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | Landing Page          | Se validará si el usuario comprende qué problema resuelve MineGuard, qué beneficios ofrece a la empresa minera y si la información presentada genera confianza para solicitar una implementación. |
    | Web Application       | Se validará si el usuario puede interpretar el dashboard, revisar alertas, identificar vehículos/conductores involucrados y reconocer acciones disponibles para atender eventos críticos.         |
    | Información operativa | Se observará si el usuario entiende datos como alertas críticas, eventos de fatiga, vehículos activos, conductores en campo y estados de atención.                                                |
    | Toma de decisiones    | Se evaluará si la información mostrada permite actuar rápidamente ante una situación de riesgo.                                                                                                   |

    **User Flows seleccionados para la validación del Segmento 1**

    | Código  | User Flow                       | Descripción del flujo                                                                                                                                                                                                |
    | ------- | ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | S1-UF01 | Exploración del Landing Page    | El usuario ingresa al Landing Page, revisa la sección inicial, explora la propuesta de solución, el funcionamiento del sistema y finalmente identifica la acción principal para acceder o solicitar más información. |
    | S1-UF02 | Acceso al Centro de Control     | El usuario ingresa a la Web Application y reconoce la pantalla principal del sistema, identificando indicadores, cards y secciones relacionadas con el monitoreo operativo.                                          |
    | S1-UF03 | Revisión de alertas críticas    | El usuario accede a la sección de alertas o identifica alertas visibles en el dashboard, revisa su nivel de criticidad, categoría, vehículos involucrados y estado actual.                                           |
    | S1-UF04 | Atención de una alerta          | El usuario selecciona una alerta crítica, interpreta la información presentada y determina qué acción debería ejecutar para mitigar el riesgo.                                                                       |
    | S1-UF05 | Consulta de flota y conductores | El usuario revisa información de vehículos, conductores o sensores para validar si puede identificar rápidamente el estado operativo de los recursos.                                                                |

<br>

+ Segmento 2: Operadores y Conductores de Vehículos Livianos

    Este segmento está conformado por conductores de camionetas de supervisión, mantenimiento, logística u otros vehículos menores que circulan dentro de operaciones mineras. Para este grupo, la validación se enfoca en comprobar si la solución comunica adecuadamente su aporte a la seguridad del conductor y si las alertas o mensajes del sistema son claros, oportunos y no generan distracción.

    | Elemento a validar   | Descripción                                                                                                                                                      |
    | -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | Landing Page         | Se validará si el conductor comprende cómo MineGuard ayuda a prevenir accidentes y proteger su integridad durante la conducción en zonas de riesgo.              |
    | Web Application      | Se validará la comprensión de información relacionada con alertas, vehículos, conductores y eventos operativos desde una perspectiva de seguridad del conductor. |
    | Alertas de seguridad | Se evaluará si los mensajes, niveles de riesgo y acciones sugeridas son fáciles de entender.                                                                     |
    | Utilidad percibida   | Se observará si el usuario considera que la solución puede ayudarlo a reaccionar mejor ante riesgos de colisión, fatiga o proximidad con maquinaria pesada.      |

    **User Flows seleccionados para la validación del Segmento 2**

    | Código  | User Flow                                         | Descripción del flujo                                                                                                                                                          |
    | ------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
    | S2-UF01 | Comprensión de la propuesta desde el Landing Page | El usuario ingresa al Landing Page, revisa la propuesta de valor y explica con sus palabras cómo MineGuard podría proteger a los conductores dentro de una operación minera.   |
    | S2-UF02 | Identificación de beneficios de seguridad         | El usuario explora las secciones informativas del Landing Page y reconoce beneficios relacionados con alertas en tiempo real, prevención de colisiones y reducción de riesgos. |
    | S2-UF03 | Interpretación de una alerta operativa            | El usuario observa una alerta dentro de la Web Application e interpreta su nivel de riesgo, el tipo de evento y la acción que debería tomar un conductor ante esa situación.   |
    | S2-UF04 | Revisión de estado de vehículo o conductor        | El usuario revisa información relacionada con vehículos o conductores para validar si el estado presentado es comprensible y útil para la operación.                           |
    | S2-UF05 | Evaluación de claridad y distracción              | El usuario evalúa si la información mostrada por el sistema sería clara en un contexto real de trabajo y si las alertas ayudan sin generar distracción excesiva.               |

+ Estructura general de la sesión de validación:

    Cada entrevista seguirá una estructura común para ambos segmentos, con ligeras variaciones según el perfil del participante.

    + Introducción: Explicar brevemente el objetivo de la sesión y el contexto de MineGuard. Además de prepara al usuario para la validación.
    + Exploración del Landing Page: El usuario debe navega por el Landing Page y comentar qué entiende de la solución. Con esto validamos la claridad de la propuesta de valor.
    + Interacción con la Web Application: El usuario realiza los user flows definidos para su segmento. Con el objetivo de validar navegación, comprensión de información y utilidad.
    + Comentarios finales: El usuario responde preguntas breves sobre claridad, confianza, utilidad y mejoras. De esta manera nosotros poder recoger insights para mejorar la solución.

+ **Preguntas guía para el segmento 1: Supervisión Corporativa en Minería de Tajo Abierto**

    Durante la revisión del Landing Page:

    1. ¿La página comunica claramente qué problema busca resolver MineGuard?
    2. ¿La propuesta de valor te parece relevante para una empresa minera?
    3. ¿Qué sección te resultó más clara o útil?
    4. ¿Qué información agregarías antes de solicitar una demo o implementación?

    Durante la revisión de la Web Application:

    1. ¿La pantalla principal permite entender rápidamente el estado de la operación?
    2. ¿Las alertas son visibles y fáciles de interpretar?
    3. ¿La clasificación de criticidad ayuda a priorizar decisiones?
    4. ¿Consideras que el sistema facilitaría una respuesta más rápida ante una posible colisión?
    5. ¿Qué información falta para que el supervisor pueda tomar una decisión con mayor seguridad?

    Preguntas finales:

    1. ¿Usarías una solución como MineGuard dentro de un centro de control?
    2. ¿Qué tan confiable te parece la información presentada?
    3. ¿Qué mejorarías en la navegación, diseño o contenido?
    4. En una escala del 1 al 5, ¿qué tan útil consideras la solución para reducir riesgos operativos?

+ **Preguntas guía para el segmento 2: Operadores y Conductores de Vehículos Livianos**

    Durante la revisión del Landing Page:

    1. ¿Te queda claro cómo este sistema podría ayudarte a evitar accidentes?
    2. ¿Qué beneficio consideras más importante como conductor?
    3. Por lo que leíste ¿La solución te parece útil para evitar accidentes con vehículos pesados o autónomos?
    4. ¿Qué información te gustaría ver antes de confiar en este sistema?

    Durante la revisión de la aplicación:

    1. Al observar una alerta en pantalla, ¿entiendes inmediatamente qué significa?
    2. ¿La información mostrada sería fácil de entender durante una jornada de trabajo?
    3. ¿Los colores, niveles de alerta o mensajes permiten reconocer rápidamente el nivel de riesgo?
    4. ¿La solución parece apoyar al conductor sin generar distracciones?
    5. ¿Qué cambiarías para que el sistema sea más práctico en campo?

    Preguntas finales:

    1. ¿Te sentirías más seguro utilizando una solución como MineGuard?
    2. ¿Qué tipo de alerta sería más efectiva para ti: visual, sonora, vibración u otra?
    3. En una escala del 1 al 5, ¿qué tan fácil te parecería usar MineGuard durante una operación real?




### 6.3.2. Registro de Entrevistas.



### 6.3.3. Evaluaciones según heurísticas
