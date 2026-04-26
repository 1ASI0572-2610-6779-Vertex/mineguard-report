<h2>4.1. Strategic-Level Domain-Driven Desing</h2>
<h3>4.1.1. Design-Level EventStorming</h3>

Event Storming es una técnica que se realiza en equipo para poder comprender y explorar todos los posibles eventos que posee un sistema. Los integrantes del equipo realizan lluvia de ideas para mapear las acciones que un usuario posiblemente realice durante el uso de la aplicación. También, con esta técnica podemos definir en grupo los procesos el diseño y las reglas de negocio e la plataforma a desarrollar. 

A continuación se mostrará los 9 pasos del Event Storming realizados en el Miro:

**Paso 1: Unstructured Exploration**

En este paso se realiza una lluvia de ideas relacionado a los eventos que posiblemente posea el sistema.

<img src="assets/Step1.png">

**Paso 2: Timelines**

En esta fase, los eventos identificados se ordenan de manera secuenial y se agrupan entre los tipos de usuario.

<img src="assets/Step2.png">

**Paso 3: Paint Points**

Durante este paso, se identifican los puntos donde se presente tráfico o también llamado cuellos de botella para poseer un plan para poder mejorar y actualizar aquellos puntos y así ofrecer una mejor experiencia a nuestros usuarios.

<img src="assets/Step3.png">


**Paso 4: Pivotal Points**

En este paso, identificamos los eventos comerciales importantes que nos indica que hay un cambio de contexto o sección en la aplicación.

<img src="assets/step4.png">

**Paso 5: Commands**

Los comandos son representaciones de la consecuencia que generó un evento o varios eventos.

<img src="assets/step5.png">

**Paso 6: Policies**

En este escenario, se muestra que un evento puede provocar la ejecución de un comando manejado por una política.

<img src="assets/step6.png">

**Paso 7: Read Models**

En este escenario, los read models sirven para generar una interfaz de lectura de un evento para que el usuario pueda decidir si ejecutar un comando o no.

<img src="assets/step7.png">

**Paso 8: External Systems**

En esta fase, se identifican los sistemas externos que usará la plataforma móvil para su ejecución eficaz.

<img src="assets/sstep8.png">

**Paso 9: Aggregates**

En este paso, con los eventos y comandos realizados, entonces ya se puede comenzar a juntar conceptos relacionados en un grupo, o mejor dicho en un bounded context.

<h3>4.1.1.1. Candidate Context Discovery</h3>

Nuestro equipo adoptó un enfoque se se centra en buscar partes del sistema que deben estar agrupados, desde un punto funcional del usuario y de infraestructura.

Se identificaron 7 Bounded Context:

- Identify and Access Management (IAM): 

En este escenario, se crea, auténtica, autoriza y gestiona los usuarios que están registrados en el sistema. Se introduce el manejo de permisos y roles, también el control de acceso a diferentes tipos de usuarios.

<img src="assets/iam_ccd.png">  

- Service Execution and Monitoring: 

Este bounded context se encarga de procesar la telemetría en tiempo real, evaluar riesgos (proximidad, colisión y fatiga) y gestionar el ciclo de vida de las alertas, determinando si deben notificarse, auto-resolverse o escalarse al supervisor.

<img src="assets/EventStorming_Service_Execution_and_Monitoring.jpg">


- Dashboards and Analytics: 

Este bounded permite recopilar, procesar y visualizar la información operativa del sistema. Analizando alertas, identificar patrones de riesgo y tomar decisiones mediante dashboards en tiempo real y análisis históricos.

<img src="assets/EventStorming_Dashboard_and_Analytics.png">

- Subscriptions and Payment Management:

Este bounded permite gestionar los planes de suscripción de los usuarios, procesar los pagos y controlar los estados de cada suscripción. Se encarga de manejar las renovaciones automáticas, garantizar la correcta facturación y facilitar el seguimiento financiero de los cobros recurrentes.

<img src="assets/EventStorming_Subscriptions_and_Payment_Management.png">

<h3>4.1.1.2. Domain Message Flows Modeling</h3>

**Escenario: Detección y Gestión de Alerta Crítica**
- Los Sensores IoT transmiten los datos de telemetría (coordenadas, velocidad) en tiempo real hacia el contexto de Service Execution and Monitoring.
- Al detectar un riesgo, el sistema dispara automáticamente una alarma sonora y visual hacia el Dispositivo de Cabina.
- El dispositivo emite la advertencia física para alertar del peligro al Conductor.
- En paralelo, el sistema envía la notificación al Web Dashboard para visibilidad del centro de control.
- El Supervisor interactúa con el dashboard para atender la alerta, lo que envía el comando de actualización de estado de vuelta al sistema.
- Finalmente, el contexto publica el evento de alerta resuelta hacia Dashboards and Analytics para el registro de tiempos de respuesta y métricas de rendimiento.

<img src="assets/flows_modeling_alert_detection_management.jpg">

**Escenario: Estado en tiempo real de conductores**
- El supervisor solicita el estado de los conductores desde el Dashboard UI.
- El contexto de Dashboards and Analytics recibe la consulta y obtiene datos del contexto Service Execution and Monitoring.
- Este último envía eventos como DriverStatusUpdated y FatigueDetected.
- El contexto de Analytics procesa la información y genera LiveDriverData.
- Finalmente, el Dashboard muestra los datos en tiempo real al supervisor.

<img src="assets/flows_modeling_real_time_status.png">

**Escenario: Visualización de alertas críticas**
- El supervisor solicita el estado de los conductores desde el Dashboard UI.
- El contexto de Dashboards and Analytics recibe la consulta y obtiene datos del contexto Service Execution and Monitoring.
- Este último envía eventos como DriverStatusUpdated y FatigueDetected.
- El contexto de Analytics procesa la información y genera LiveDriverData.
- Finalmente, el Dashboard muestra los datos en tiempo real al supervisor.

<img src="assets/flows_modeling_alert_views.png">


<h3>4.1.1.3. Bounded Context Canvases</h3>

En esta sección se demuestra el proceso que ejecutó el equipo para agrupar los bounded context que posee nuesdtro sdisdtema. El desarrollo de aquellos se realizó minuciosamente para comprobar de qué son los bounded context que reflejan el dominio del negocio. De esta manera, se logró formar 7 bounded context, enfocándonos en que cada uno de ellos resuelva la necesidad del usuario.

- Bounded Context Canvases Identity and Access Management (IAM)

<img src="assets/iam2.0.png">

- Bounded Context Canvas Service Execution and Monitoring

<img src="assets/BC_Canvases_Service_Execution_and_Monitoring.jpg">

- Bounded Context Canvases Dashboards and Analytics

<img src="assets/BC_Canvases_Dashboards_and_Analytics.png">

- Subscriptions and Payment Management

<img src="assets/BC_Canvases_Subscriptions_and_Payment_Management.png">


