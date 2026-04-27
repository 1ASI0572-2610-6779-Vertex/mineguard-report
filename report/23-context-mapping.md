<!--D d-->
<!--
1. Shared Kernel (Núcleo Compartido)
Es un subconjunto del dominio que dos o más equipos acuerdan compartir. Puede ser código o una base de datos.
2. Customer/Supplier (Cliente/Proveedor)
Establece una jerarquía donde el Proveedor (Upstream) entrega datos o servicios que el Cliente (Downstream) necesita.
3. Conformist (Conformista)
Ocurre cuando el contexto Downstream decide adaptarse ciegamente al modelo del contexto Upstream.
4. Anti-corruption Layer (ACL - Capa Anticorrupción)
Es el patrón más defensivo. El contexto Downstream crea una capa de traducción para evitar que los conceptos "ajenos" del proveedor contaminen su propio modelo de dominio.
-->
<h2>4.1.2. Context Mapping</h2>

En esta parte, se explican las relaciones entre los 7 bounded contexs identificados de nuestro sistema.

<h3>- IAM -> SPM</h3> 

Descripción:

SPM gestiona si el usuario está autenticado para procesar un pago. IAM provee la identidad.

Patrón:

IAM actúa como proveedor de identidad. Subscription usa una **Anti-corruption** Layer para traducir los tokens de identidad.

<h3>- IAM -> PPM</h3>

Descripción:

PPM depende del identificador único uuid que genera iam para asociar los datos del perfil al usuario correcto. Gestiona el perfil y da los roles adecuados para permitir el acceso y modificación de perfil. 

Patrón:

Profiles suele ser **Conformist** con IAM, ya que depende totalmente de un usuario creado para poder existir

<h3>- SPM -> PPM</h3>

Descripción:

Comparte información sobre el "Estado del cliente". Si un usuario cambia su plan (SPM), esto puede desbloquear preferencias premium.

Patrón:

Relación de **Customer-Supplier**. Si el estado de suscripción cambia a Premium, el contexto de Profiles permite habilitar preferencias extendidas. 

<h3>- SDP -> SEM</h3>

Descripción:

La planificación define rutas y horarios; la ejecución debe obedecer este plan de forma que se garantiza un proceso eficaz en el transporte de los camiones dentro de la mina. Además se define los nodos para que los sensores no pierdan el alcanze que se necesita para monitorear a los vehiculos. 

Patrón:

**Customer-Supplier** porque el monitoreo no puede inventarse rutas estas deben seguir un diselo planificadó.

<h3>- RAM -> SEM</h3>

Descripción:

Comparten información crítica sobre el estado de los sensores por telemetría y vehículos en tiempo real. 

Patrón:

**Shared Kernel** porque para evitar duplicar código complejo de telemetría, ambos equipos comparten librerías en común que definen los estados del hardware.

<h3>- SEM -> DA</h3>

Descripción:

El Dashboard se limita a mostrar los datos tal como la ejecución los genera, de forma que se permite ver los detalles del funcionamiento tanto sensores como trabajadores de la empresa.

Patrón:

**Conformist** porque simplemente se conforma con la estructura de datos que envía el motor de ejecución. 

<h3>>> Preguntas estratégicas de reflexión:</h3>

- ¿ Qué pasaría si juntamos IAM con PPM ?

No sería ideal juntarlos, debido a que ambos tienen responsabilidades diferentes. IAM se encarga de la autorizaión, autenticacióon y permisos de los usuarios mientras que la gdestión de perfil maneja la información personal de cada tipo de cuenta.

- ¿ Qué pasaría si creamos un Shared Service para la Telemetría ?

Actualmente se posee un shared kernel entre RAM y SEM. <br>
Si el sistema crece, ese kernel compartido podría volverse un cuello de botella para el despliegue. Mover esa funcionaldad a un contexto de shared service permitiría que RAM y SEM escalen de forma independiente.

- ¿Qué pasaría si el Dashboard (DA) deja de ser un Conformist?

Si el Dashboard (DA) deja de ser un Conformist, pasaría de ser un "espectador pasivo" que acepta lo que le den, a tener voz propia sobre cómo quiere recibir y procesar la información, dejar de ser Conformist le da autonomía, pero obliga a trabajar más en la infraestructura de datos.

- ¿Qué pasaría si el Bounded Context de Pagos (SPM) falla? ¿Debería el Dashboard (DA) dejar de mostrar datos en tiempo real, o el sistema de seguridad es lo suficientemente crítico como para ignorar el estado de la suscripción en una emergencia?

El sistema detecta la falla del módulo de pagos y activa un permiso temporal (o "Fail-open"). El Dashboard sigue mostrando la telemetría crítica de SEM, pero quizás se deshabilitaría funciones secundarias como reportes históricos o analítica avanzada.