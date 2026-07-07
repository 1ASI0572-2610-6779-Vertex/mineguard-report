### 6.2.3. Sprint 3

#### 6.2.3.1. Sprint Planning 3

En esta sección se presenta el resumen de la reunión de Sprint Planning correspondiente al Sprint 3 del proyecto MineGuard. Durante esta sesión, el equipo revisó el avance acumulado de los Sprints anteriores, identificó las funcionalidades pendientes del Product Backlog y definió el alcance final de la iteración para consolidar una versión más completa de la solución.

El objetivo principal de esta reunión fue priorizar las User Stories orientadas al cierre funcional del producto, enfocándose en seguridad de acceso, gestión de sesiones, comunicación entre supervisor y conductor, actualización de información operativa, análisis del desempeño del conductor, seguimiento de comportamiento y recomendaciones inteligentes ante alertas. Asimismo, se incluyó la mejora de la experiencia informativa para operadores y conductores dentro de la Landing Page.

| Sprint #                             | Sprint 3                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Sprint Planning Background**       | Tercera iteración del proyecto, enfocada en completar las funcionalidades pendientes del Product Backlog y consolidar los flujos finales de seguridad, operación, comunicación y análisis del comportamiento del conductor dentro de MineGuard.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **Date**                             | 2026-06-20                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **Time**                             | 08:00 PM                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **Location**                         | Virtual Meeting (Google Meet / Discord)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **Prepared By**                      | Rodrigo Alaya                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **Attendees (to planning meeting)**  | Rodrigo Alaya / Jorge Guevara / Gabriel Gordon / Russell Romero / Marcia Melgarejo / Renato Zegarra / Javier Gonzales                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| **Sprint n−1 Review Summary**        | Durante el Sprint 2 se consolidó la integración funcional entre dispositivos IoT, servicios backend, Edge Service, Web Application, Mobile App y Landing Page. Se implementaron funcionalidades clave relacionadas con telemetría, alertas de proximidad, colisión, fatiga, botón de pánico, monitoreo en tiempo real, reportes, analíticas y gestión de recursos.                                                                                                                                                                                                                                                                                                                                                                 |
| **Sprint n−1 Retrospective Summary** | El equipo identificó la necesidad de cerrar las funcionalidades pendientes del Product Backlog, mejorar la trazabilidad entre tareas y User Stories, reforzar los flujos de seguridad y sesión, y completar funcionalidades orientadas a la experiencia final del conductor y del supervisor.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **Sprint Goal & User Stories**       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **Sprint n Goal**                    | Our focus is on completing the final operational and safety experience of MineGuard by strengthening user access, vehicle session closure, supervisor-driver communication, driver behavior analysis, and safety recommendations. We believe it delivers a safer and more controlled mining operation to drivers and supervisors by enabling secure access, clearer responses to alerts, better operational traceability, and improved preventive decision-making. This will be confirmed when supervisors can authenticate and manage operational information, drivers can close their sessions and receive actionable recommendations, and the system can track driver behavior and action compliance based on generated alerts. |
| **Sprint n Velocity**                | 54 Story Points                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **Sum of Story Points**              | 54 Story Points                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | 

+ User Stories included in Sprint 3:

| Order | User Story Id | Title                                         | Description                                                                                                                                                     | Story Points |
| ----- | ------------: | --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | -----------: |
| 1     |          US04 | Consulta de desempeño del conductor           | Como conductor quiero visualizar mi desempeño histórico para conocer mi comportamiento en la operación.                                                         |            5 |
| 2     |          US11 | Comunicación con conductor                    | Como supervisor quiero comunicarme con el conductor tras una alerta para coordinar acciones inmediatas.                                                         |            5 |
| 3     |          US17 | Actualización de información                  | Como supervisor quiero actualizar datos de conductores y vehículos para mantener la información correcta.                                                       |            5 |
| 4     |          US21 | Recomendación de acción para el conductor     | Como conductor quiero recibir indicaciones claras ante alertas para reaccionar correctamente durante la conducción.                                             |            5 |
| 5     |          US22 | Confirmación de acción del conductor          | Como supervisor quiero verificar si el conductor responde a las alertas para validar el cumplimiento de seguridad.                                              |            8 |
| 6     |          US23 | Seguimiento de comportamiento del conductor   | Como supervisor quiero evaluar el comportamiento del conductor para identificar conductas de riesgo.                                                            |            8 |
| 7     |          US29 | Explorar herramientas de seguridad personal   | Como visitante del segmento de Operadores y Conductores quiero conocer las herramientas de seguridad disponibles para entender cómo se protegerá mi integridad. |            3 |
| 8     |          US31 | Inicio de sesión del supervisor               | Como supervisor quiero iniciar sesión en el sistema para acceder al centro de control y gestionar la operación en tiempo real.                                  |            5 |
| 9     |          US41 | Cambio de contraseña obligatorio              | Como usuario quiero actualizar mi clave temporal en el primer ingreso para asegurar la privacidad de mi cuenta.                                                 |            5 |
| 10    |          US42 | Cierre de sesión y desvinculación de vehículo | Como conductor quiero cerrar mi sesión al terminar mi jornada para desvincularme legalmente del vehículo asignado.                                              |            5 |


#### 6.2.3.2. Aspect Leaders and Collaborators

Durante el Sprint 3 del proyecto MineGuard, el equipo definió una nueva distribución de responsabilidades con el objetivo de organizar el trabajo correspondiente a las funcionalidades finales del producto. A diferencia de los sprints anteriores, esta iteración se enfocó principalmente en completar flujos pendientes relacionados con seguridad de acceso, cierre de sesión, comunicación entre supervisor y conductor, actualización de información operativa, análisis del desempeño del conductor, recomendaciones de seguridad y mejoras en la experiencia informativa para operadores.

Con el fin de mantener claridad en la comunicación interna y asegurar una adecuada asignación de responsabilidades, se elaboró una Leadership-and-Collaboration Matrix (LACX). En esta matriz, el rol Leader (L) representa al integrante responsable de dirigir el aspecto asignado, tomar decisiones funcionales o técnicas y coordinar las tareas relacionadas. El rol Collaborator (C) representa a los integrantes que participaron en el análisis, implementación, integración o validación de dicho aspecto.

| Team Member (Last Name, First Name) | GitHub Username | Security & Session Management | Driver Operations & Vehicle Session | Driver Performance & Behavior Analytics | Supervisor-Driver Communication | Safety Recommendations & Action Compliance | Resource Information Management | Landing Page / Operator Experience |
|-------------------------------------|-----------------|-------------------------------|-------------------------------------|-----------------------------------------|---------------------------------|---------------------------------------------|---------------------------------|------------------------------------|
| Alaya, Rodrigo                      | ALAYA1803       | C                             | C                                   | **L**                                   | C                               | C                                           | C                               | C                                  |
| Gordon, Gabriel                     | Silent343       | **L**                             | C                                   | C                                       | C                               | C                                           | C                               | C                             |
| Guevara, Jorge                      | Jorgito170      | C                             | **L**                                   | C                                       | C                               | C                                           | C                           | C                                  |
| Melgarejo, Marcia                   | Mevi1217        | C                             | C                                   | C                                       | **L**                           | C                                           | C                               | C                                  |
| Zegarra, Renato                     | ReiZCode        | C                             | C                                   | C                                       | C                               | **L**                                       | C                               | C                                  |
| Gonzales, Javier                    | WoodsDos        | C                         | C                                   | C                                       | C                               | C                                           | **L**                               | C                                  |
| Romero, Russell                     | RussellUPC      | C                             | C                               | C                                       | C                               | C                                           | C                               | **L**                                  |


#### 6.2.3.3. Sprint Backlog 3

Durante el desarrollo del Sprint 3 del proyecto MineGuard, se definió y gestionó el Sprint Backlog con el objetivo de completar las funcionalidades pendientes del Product Backlog general. Este Sprint se enfocó principalmente en fortalecer los flujos de seguridad, autenticación, cierre de sesión, comunicación entre supervisores y conductores, actualización de información operativa, análisis del comportamiento del conductor y recomendaciones inteligentes ante situaciones de riesgo.

Asimismo, se consideró la culminación de funcionalidades orientadas a la experiencia del usuario en la Landing Page, especialmente aquellas dirigidas al segmento de operadores y conductores. De esta manera, el Sprint 3 permitió cerrar brechas funcionales identificadas en los Sprints anteriores y consolidar una versión más completa de la solución MineGuard.

Para la gestión y seguimiento de las actividades, se utilizó Trello como herramienta de control ágil, permitiendo organizar las User Stories priorizadas y su respectiva descomposición en Work-items/Tasks, asegurando trazabilidad, asignación de responsabilidades y control del progreso del Sprint.

<br>

Link Trello: `Agregar enlace del tablero Sprint 3`

<br>

| Sprint # | User Story Id | Título de User Story                          | Work-Item / Task Id | Título del Work-Item / Task                            | Descripción                                                                                                                      | Estimación (Horas) | Asignado a       | Estado |
| -------- | ------------- | --------------------------------------------- | ------------------- | ------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------- | -----------------: | ---------------- | ------ |
| Sprint 3 | US04          | Consulta de desempeño del conductor           | US04-001            | Diseñar vista de desempeño del conductor               | Crear una pantalla donde el conductor pueda consultar métricas históricas de alertas, incidencias y cumplimiento de acciones.    |                  3 | Rodrigo Alaya    | Done   |
| Sprint 3 | US04          | Consulta de desempeño del conductor           | US04-002            | Implementar consulta de historial operativo            | Integrar la vista con los registros históricos asociados al conductor autenticado.                                               |                  3 | Jorge Guevara    | Done   |
| Sprint 3 | US04          | Consulta de desempeño del conductor           | US04-003            | Actualizar métricas tras nuevos eventos                | Registrar automáticamente nuevos eventos de conducción para mantener actualizado el desempeño del conductor.                     |                  2 | Gabriel Gordon   | Done   |
| Sprint 3 | US11          | Comunicación con conductor                    | US11-001            | Diseñar flujo de comunicación desde alerta             | Agregar una acción en el panel de alertas que permita al supervisor iniciar comunicación con el conductor asociado.              |                  3 | Marcia Melgarejo | Done   |
| Sprint 3 | US11          | Comunicación con conductor                    | US11-002            | Implementar envío de notificación al conductor         | Desarrollar la lógica para enviar una notificación o mensaje operativo al dispositivo del conductor.                             |                  3 | Renato Zegarra   | Done   |
| Sprint 3 | US11          | Comunicación con conductor                    | US11-003            | Registrar intento de contacto                          | Guardar fecha, hora, conductor, alerta asociada y resultado del intento de comunicación.                                         |                  2 | Javier Gonzales  | Done   |
| Sprint 3 | US11          | Comunicación con conductor                    | US11-004            | Manejar fallos de comunicación                         | Mostrar mensaje de error y permitir reintentar el envío cuando exista un problema de conectividad.                               |                  2 | Russell Romero   | Done   |
| Sprint 3 | US17          | Actualización de información                  | US17-001            | Habilitar edición de conductores                       | Permitir que el supervisor actualice datos de conductores registrados, validando campos obligatorios y formatos.                 |                  3 | Rodrigo Alaya    | Done   |
| Sprint 3 | US17          | Actualización de información                  | US17-002            | Habilitar edición de vehículos                         | Permitir que el supervisor actualice información de vehículos, incluyendo estado, placa, tipo y datos operativos.                |                  3 | Jorge Guevara    | Done   |
| Sprint 3 | US17          | Actualización de información                  | US17-003            | Registrar fecha de modificación                        | Guardar la fecha de modificación y el usuario responsable de cada actualización realizada.                                       |                  2 | Gabriel Gordon   | Done   |
| Sprint 3 | US17          | Actualización de información                  | US17-004            | Validar errores de actualización                       | Rechazar cambios con datos inválidos y mostrar mensajes de corrección al supervisor.                                             |                  2 | Marcia Melgarejo | Done   |
| Sprint 3 | US21          | Recomendación de acción para el conductor     | US21-001            | Definir reglas de recomendación por tipo de alerta     | Establecer recomendaciones específicas para proximidad, colisión, fatiga y pánico.                                               |                  3 | Renato Zegarra   | Done   |
| Sprint 3 | US21          | Recomendación de acción para el conductor     | US21-002            | Mostrar recomendación preventiva en cabina             | Presentar mensajes como reducir velocidad, mantener distancia o estar alerta ante riesgos preventivos.                           |                  3 | Javier Gonzales  | Done   |
| Sprint 3 | US21          | Recomendación de acción para el conductor     | US21-003            | Mostrar recomendación crítica en cabina                | Presentar mensajes de acción inmediata, como detenerse, ante alertas críticas de colisión o fatiga severa.                       |                  3 | Russell Romero   | Done   |
| Sprint 3 | US21          | Recomendación de acción para el conductor     | US21-004            | Asociar recomendación al evento generado               | Guardar la recomendación aplicada junto con la alerta correspondiente para análisis posterior.                                   |                  2 | Rodrigo Alaya    | Done   |
| Sprint 3 | US22          | Confirmación de acción del conductor          | US22-001            | Definir criterios de cumplimiento ante alertas         | Establecer condiciones para determinar si el conductor respondió correctamente, como reducir velocidad o detenerse.              |                  3 | Jorge Guevara    | Done   |
| Sprint 3 | US22          | Confirmación de acción del conductor          | US22-002            | Implementar validación de respuesta del conductor      | Comparar la telemetría posterior a la alerta con la acción esperada para determinar cumplimiento.                                |                  4 | Gabriel Gordon   | Done   |
| Sprint 3 | US22          | Confirmación de acción del conductor          | US22-003            | Registrar cumplimiento o incumplimiento                | Guardar el resultado de la respuesta del conductor asociado al evento de alerta.                                                 |                  2 | Marcia Melgarejo | Done   |
| Sprint 3 | US22          | Confirmación de acción del conductor          | US22-004            | Mantener alerta activa ante incumplimiento             | Mantener visible la alerta crítica cuando el conductor no ejecute la acción esperada.                                            |                  2 | Renato Zegarra   | Done   |
| Sprint 3 | US23          | Seguimiento de comportamiento del conductor   | US23-001            | Definir modelo de clasificación de comportamiento      | Crear criterios para clasificar al conductor como seguro, preventivo o riesgoso según su historial operativo.                    |                  3 | Javier Gonzales  | Done   |
| Sprint 3 | US23          | Seguimiento de comportamiento del conductor   | US23-002            | Calcular indicadores de comportamiento                 | Procesar alertas, incidencias, confirmaciones de acción y eventos frecuentes para generar indicadores.                           |                  4 | Russell Romero   | Done   |
| Sprint 3 | US23          | Seguimiento de comportamiento del conductor   | US23-003            | Visualizar comportamiento en dashboard                 | Mostrar la clasificación del conductor dentro del panel del supervisor para facilitar seguimiento preventivo.                    |                  3 | Rodrigo Alaya    | Done   |
| Sprint 3 | US23          | Seguimiento de comportamiento del conductor   | US23-004            | Resaltar conductores de riesgo                         | Identificar visualmente a los conductores con comportamientos críticos o reincidentes.                                           |                  2 | Jorge Guevara    | Done   |
| Sprint 3 | US29          | Explorar herramientas de seguridad personal   | US29-001            | Diseñar sección de herramientas para operadores        | Crear una sección en la Landing Page orientada a operadores y conductores, explicando las herramientas de seguridad disponibles. |                  2 | Gabriel Gordon   | Done   |
| Sprint 3 | US29          | Explorar herramientas de seguridad personal   | US29-002            | Presentar beneficios operativos de seguridad           | Mostrar beneficios como alertas en cabina, monitoreo de fatiga, botón de pánico y retroalimentación inmediata.                   |                  2 | Marcia Melgarejo | Done   |
| Sprint 3 | US29          | Explorar herramientas de seguridad personal   | US29-003            | Adaptar contenido a versión responsive                 | Asegurar que la sección pueda visualizarse correctamente en dispositivos móviles y pantallas pequeñas.                           |                  2 | Renato Zegarra   | Done   |
| Sprint 3 | US31          | Inicio de sesión del supervisor               | US31-001            | Diseñar formulario de inicio de sesión del supervisor  | Crear la interfaz de login para supervisores con campos de usuario y contraseña.                                                 |                  3 | Javier Gonzales  | Done   |
| Sprint 3 | US31          | Inicio de sesión del supervisor               | US31-002            | Integrar autenticación del supervisor                  | Conectar el formulario con el servicio de autenticación para validar credenciales registradas.                                   |                  3 | Russell Romero   | Done   |
| Sprint 3 | US31          | Inicio de sesión del supervisor               | US31-003            | Redirigir al centro de control                         | Permitir el acceso al dashboard operativo cuando el supervisor se autentique correctamente.                                      |                  2 | Rodrigo Alaya    | Done   |
| Sprint 3 | US31          | Inicio de sesión del supervisor               | US31-004            | Mostrar error por credenciales inválidas               | Rechazar el acceso cuando las credenciales sean incorrectas y mostrar un mensaje de error de autenticación.                      |                  2 | Jorge Guevara    | Done   |
| Sprint 3 | US41          | Cambio de contraseña obligatorio              | US41-001            | Detectar uso de contraseña temporal                    | Identificar cuando un usuario inicia sesión por primera vez con credenciales temporales.                                         |                  3 | Gabriel Gordon   | Done   |
| Sprint 3 | US41          | Cambio de contraseña obligatorio              | US41-002            | Mostrar formulario obligatorio de cambio de contraseña | Bloquear el acceso a funciones operativas hasta que el usuario actualice su contraseña inicial.                                  |                  3 | Marcia Melgarejo | Done   |
| Sprint 3 | US41          | Cambio de contraseña obligatorio              | US41-003            | Validar requisitos de nueva contraseña                 | Verificar longitud mínima, confirmación, complejidad y diferencia respecto a la clave temporal.                                  |                  3 | Renato Zegarra   | Done   |
| Sprint 3 | US41          | Cambio de contraseña obligatorio              | US41-004            | Permitir acceso tras actualización exitosa             | Actualizar el estado del usuario y permitir el ingreso al sistema después de cambiar la contraseña.                              |                  2 | Javier Gonzales  | Done   |
| Sprint 3 | US42          | Cierre de sesión y desvinculación de vehículo | US42-001            | Implementar cierre de sesión del conductor             | Agregar opción para que el conductor cierre sesión al finalizar su jornada operativa.                                            |                  3 | Russell Romero   | Done   |
| Sprint 3 | US42          | Cierre de sesión y desvinculación de vehículo | US42-002            | Validar estado del vehículo antes del cierre           | Verificar que el vehículo se encuentre detenido antes de permitir el cierre de sesión.                                           |                  3 | Rodrigo Alaya    | Done   |
| Sprint 3 | US42          | Cierre de sesión y desvinculación de vehículo | US42-003            | Liberar vehículo asignado                              | Desvincular al conductor del vehículo y cambiar la unidad a estado disponible para futuras operaciones.                          |                  3 | Jorge Guevara    | Done   |
| Sprint 3 | US42          | Cierre de sesión y desvinculación de vehículo | US42-004            | Registrar hora de fin de operación                     | Guardar la fecha y hora de cierre de sesión para mantener trazabilidad de la jornada.                                            |                  2 | Gabriel Gordon   | Done   |


#### 6.2.3.4. Development Evidence for Sprint Review

Durante el Sprint 3 del proyecto MineGuard, el equipo completó la implementación de las funcionalidades planificadas para esta iteración, fortaleciendo los diferentes componentes de la solución, incluyendo la Landing Page, Web Application, Web Services, Mobile Application, Edge Service, Embedded Application y Prototype. Los avances estuvieron enfocados en completar los flujos de autenticación, gestión de sesiones, comunicación entre supervisor y conductor, análisis del comportamiento del conductor, recomendaciones de seguridad y mejoras en la experiencia de usuario. A continuación, se presentan los repositorios y los commits que evidencian las implementaciones realizadas durante este Sprint.


+ **Web Service:**

+ **Web Service:**

| Repository | Branch | Commit Id | Commit Message | Commit Message Body | Committed on (Date) |
|---|---|---|---|---|---|
| MineGuard-WebService | feature/restful-endpoints | `cfb5f73` | fix: fix a send email on brevo | Fixed email sending integration using Brevo service. | Jul 2, 2026 |
| MineGuard-WebService | feature/restful-endpoints | `a8787ba` | fix: correction email autorization | Corrected email authorization configuration for notification delivery. | Jul 2, 2026 |
| MineGuard-WebService | feature/restful-endpoints | `38c6450` | fix: address personal change | Updated personal address data handling in service records. | Jul 2, 2026 |
| MineGuard-WebService | feature/restful-endpoints | `8c600d7` | fix: dataseeder commit | Updated DataSeeder configuration and initial test data. | Jul 2, 2026 |
| MineGuard-WebService | feature/restful-endpoints | `9912f47` | fix: vehicle operational string | Fixed vehicle operational status value handling. | Jul 2, 2026 |
| MineGuard-WebService | feature/restful-endpoints | `d7880e6` | feat: fix backend connection | Improved backend connection configuration for service integration. | Jul 4, 2026 |
| MineGuard-WebService | feature/restful-endpoints | `ec087ec` | fix: Implementation of RESTful endpoints and service refactoring | Implemented RESTful endpoints and refactored service structure. | Jul 4, 2026 |
| MineGuard-WebService | feature/restful-endpoints | `a854a87` | Fixr: Cleaning up duplicate controllers and resolving ambiguous mapping | Removed duplicate controllers and fixed ambiguous endpoint mappings. | Jul 4, 2026 |
| MineGuard-WebService | feature/restful-endpoints | `ffacab4` | fix:adreess correct port | Corrected application port configuration for service execution. | Jul 4, 2026 |
| MineGuard-WebService | feature/restful-endpoints | `c568035` | fix:change valued of tables | Adjusted database table values and seed records. | Jul 4, 2026 |
| MineGuard-WebService | feature/restful-endpoints | `4a77c73` | fix: application properties | Updated application properties for environment configuration. | Jul 4, 2026 |
| MineGuard-WebService | feature/restful-endpoints | `d54d20d` | feature: add new parametre of suscription | Added new subscription parameter for company registration flow. | Jul 5, 2026 |
| MineGuard-WebService | feature/restful-endpoints | `8c600d7` | fix: id of generate reports | Fixed generated report identifier handling. | Jul 5, 2026 |
| MineGuard-WebService | feature/restful-endpoints | `9912f47` | fix: add new parametres of device sensors | Added new device sensor parameters for telemetry records. | Jul 5, 2026 |

+ **Web App:**

| Repository       | Branch                   | Commit Id | Commit Message                                                | Commit Message Body                                                                       | Committed on (Date) |
| ---------------- | ------------------------ | --------- | ------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ------------------- |
| MineGuard-WebApp | hotfix/deploy-webapp     | `8c37de0` | fix: update angular build budgets                             | Updated Angular build budgets to optimize the application build process.                  | Jun 25, 2026        |
| MineGuard-WebApp | feature/register-company | `1f2a523` | fix: refactor all end points and add register companie screen | Refactored frontend service endpoints and implemented the company registration interface. | Jul 5, 2026         |
| MineGuard-WebApp | feature/register-company | `0ce169b` | fix: change kpis tokens for iam                               | Updated KPI authentication tokens to integrate with the new IAM module.                   | Jul 5, 2026         |
| MineGuard-WebApp | feature/register-company | `42fead1` | feat: integrate a new tab of create a device                  | Added a new interface for registering and managing IoT devices.                           | Jul 5, 2026         |
| MineGuard-WebApp | feature/register-company | `1421660` | fix: style and hardcode                                       | Adjusted UI styles and corrected hardcoded values in the application.                     | Jul 6, 2026         |


+ **Landing Page:**

+ **Mobile App:**

+ **Embbeded App:**

| Repository            | Branch                                | Commit Id | Commit Message                                      | Commit Message Body                                                                                              | Committed on (Date) |
| --------------------- | ------------------------------------- | --------- | --------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ------------------- |
| MineGuard-EmbeddedApp | fix/sensors-actuators-errors          | `9180b57` | fix: fixed some features about sensor and actuators | Fixed issues related to sensor readings and actuator behavior to improve device stability.                       | Jul 1, 2026         |
| MineGuard-EmbeddedApp | feature/Integrate-framework-modestiot | `06e6085` | feat: integrate the library modestiot               | Integrated the ModestIoT framework into the embedded application to improve device communication and management. | Jul 4, 2026         |
| MineGuard-EmbeddedApp | fix/fixed-edge-connection             | `de4c000` | feat: added edge connection                         | Implemented the communication layer between the embedded device and the Edge Service.                            | Jul 5, 2026         |


+ **Edge Service:**

| Repository            | Branch             | Commit Id | Commit Message                                                                | Commit Message Body                                                              | Committed on (Date) |
| --------------------- | ------------------ | --------- | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | ------------------- |
| MineGuard-EmbeddedApp | feature/iam        | `d80b83d` | feat: add application layer                                                   | Added application layer for device authentication.                               | Jun 19, 2026        |
| MineGuard-EmbeddedApp | feature/iam        | `534077e` | feat: add domain layer                                                        | Added domain layer for device authentication.                                    | Jun 19, 2026        |
| MineGuard-EmbeddedApp | feature/iam        | `c586035` | feat: add infrastructure layer                                                | Added infrastructure layer for device authentication.                            | Jun 19, 2026        |
| MineGuard-EmbeddedApp | feature/iam        | `4a77c73` | feat: add interfaces layer                                                    | Added interfaces layer for device authentication.                                | Jun 19, 2026        |
| MineGuard-EmbeddedApp | feature/iam        | `9a3ac50` | fix(): Add IAM services                                                       | Implemented IAM services and related fixes.                                      | Jun 19, 2026        |
| MineGuard-EmbeddedApp | feature/iam        | `68d270e` | feat(): Add IAM entities                                                      | Added IAM entities for device authentication.                                    | Jun 19, 2026        |
| MineGuard-EmbeddedApp | feature/iam        | `f7d5418` | feat(iam): add infrastructure and interfaces layers for device authentication | Completed infrastructure and interface implementation for device authentication. | Jun 19, 2026        |
| MineGuard-EmbeddedApp | feature/monitoring | `2cb7c5d` | feat(): add monitoring features to edge                                       | Implemented monitoring features for the embedded edge device.                    | Jun 20, 2026        |
| MineGuard-EmbeddedApp | feature/monitoring | `a854a87` | Feature: Update monitoring                                                    | Updated monitoring functionalities and operational logic.                        | Jun 20, 2026        |
| MineGuard-EmbeddedApp | feature/planning   | `d54d20d` | feat: add bounded planning and subscriptions                                  | Added planning module and subscription management components.                    | Jun 20, 2026        |
| MineGuard-EmbeddedApp | develop            | `d7880e6` | feat: fix backend connection                                                  | Updated backend connection and integration settings.                             | Jul 5, 2026         |
| MineGuard-EmbeddedApp | develop            | `ec087ec` | feat: Add Swagger and Render configuration                                    | Added API documentation and Render deployment configuration.                     | Jul 5, 2026         |
| MineGuard-EmbeddedApp | release/2.0.0      | `8eeb650` | fix: restore Render configuration from release/2.0.0                          | Restored the Render deployment configuration for the final release.              | Jul 5, 2026         |



+ **Prototype:**




#### 6.2.3.5. Testing Suite Evidence for Sprint Review.

Durante el Sprint 3 del proyecto MineGuard se diseñó una suite de pruebas orientada a validar las funcionalidades finales comprometidas en la iteración. Estas pruebas se enfocaron en los flujos de autenticación del supervisor, cambio obligatorio de contraseña, cierre de sesión del conductor, desvinculación de vehículo, comunicación entre supervisor y conductor, actualización de información operativa, consulta de desempeño, seguimiento del comportamiento del conductor, recomendaciones de seguridad y confirmación de acciones ante alertas.

La suite de testing incluye **Unit Tests**, **Integration Tests** y **Acceptance Tests bajo enfoque BDD**, con el objetivo de asegurar que las reglas de negocio, servicios de aplicación, endpoints REST y flujos funcionales del sistema respondan correctamente a los escenarios definidos en las User Stories del Sprint 3.

**Testing repository:** `https://github.com/1ASI0572-2610-6779-Vertex/mineguard-webservice`

##### Unit Tests

###### Unit Test Record 01

Se implementó el Unit Test **SupervisorAuthenticationServiceImplTest** con el objetivo de validar la lógica de autenticación del supervisor y las restricciones asociadas al primer ingreso con contraseña temporal.

Este test se relaciona con las **User Stories US31** y **US41**, orientadas al inicio de sesión del supervisor y al cambio obligatorio de contraseña.

Los comportamientos validados fueron:

- Inicio de sesión exitoso del supervisor con credenciales válidas.
- Rechazo de credenciales inválidas.
- Identificación de usuarios que ingresan por primera vez con contraseña temporal.
- Restricción de acceso a funcionalidades operativas hasta completar el cambio de contraseña.

Ruta del test:

```plaintext
src/test/java/com/mineguard/platform/iam/application/internal/commandservices/SupervisorAuthenticationServiceImplTest.java
```

![unit-test-01](../report/assets/evidence-sprint3/testing/unit-test-01-supervisor-auth.png)

###### Unit Test Record 02

Se implementó el Unit Test **DriverSessionCommandServiceImplTest** con el objetivo de validar la lógica de cierre de sesión del conductor y la desvinculación del vehículo asignado al finalizar la jornada operativa.

Este test se relaciona con la **User Story US42**, orientada al cierre de sesión y desvinculación de vehículo.

Los comportamientos validados fueron:

- Cierre correcto de sesión cuando el vehículo se encuentra detenido.
- Bloqueo del cierre de sesión cuando el vehículo reporta movimiento.
- Liberación del vehículo para futuras operaciones.
- Registro de la hora de fin de la operación.

Ruta del test:

```plaintext
src/test/java/com/mineguard/platform/operations/application/internal/commandservices/DriverSessionCommandServiceImplTest.java
```

![unit-test-02](../report/assets/evidence-sprint3/testing/unit-test-02-driver-session.png)

###### Unit Test Record 03

Se implementó el Unit Test **DriverPerformanceQueryServiceImplTest** con el objetivo de validar el cálculo de métricas históricas del conductor y la clasificación de su comportamiento operativo a partir de alertas, incidentes y acciones cumplidas.

Este test se relaciona con las **User Stories US04** y **US23**, orientadas a la consulta de desempeño del conductor y seguimiento de comportamiento.

Los comportamientos validados fueron:

- Consulta de desempeño histórico por conductor.
- Agregación de alertas, incidencias y acciones cumplidas.
- Actualización automática de métricas ante nuevos eventos.
- Clasificación del conductor según comportamiento seguro, preventivo o riesgoso.

Ruta del test:

```plaintext
src/test/java/com/mineguard/platform/analytics/application/internal/queryservices/DriverPerformanceQueryServiceImplTest.java
```

![unit-test-03](../report/assets/evidence-sprint3/testing/unit-test-03-performance-behavior.png)

###### Unit Test Record 04

Se implementó el Unit Test **AlertRecommendationServiceImplTest** con el objetivo de validar la generación de recomendaciones automáticas para el conductor y la confirmación de acciones esperadas tras una alerta crítica o preventiva.

Este test se relaciona con las **User Stories US21** y **US22**, orientadas a la recomendación de acción para el conductor y confirmación de cumplimiento.

Los comportamientos validados fueron:

- Generación de recomendaciones preventivas ante alertas de proximidad.
- Generación de recomendaciones críticas ante riesgo de colisión o fatiga severa.
- Asociación de la recomendación generada con el evento de alerta.
- Evaluación de telemetría posterior para validar si el conductor respondió correctamente.

Ruta del test:

```plaintext
src/test/java/com/mineguard/platform/monitoring/application/internal/domainservices/AlertRecommendationServiceImplTest.java
```

![unit-test-04](../report/assets/evidence-sprint3/testing/unit-test-04-recommendation-compliance.png)

---

##### Integration Tests

###### Integration Test Record 01

Se ejecutó una prueba de integración sobre el endpoint **POST /api/v1/sessions/supervisor**, perteneciente al módulo IAM. El objetivo fue validar que el Web Service permita el inicio de sesión de supervisores autorizados y rechace credenciales inválidas.

Este test se relaciona con la **User Story US31**.

Comportamiento validado:

- El endpoint permite el acceso cuando las credenciales del supervisor son válidas.
- El backend retorna un token de sesión y datos básicos del usuario autenticado.
- El endpoint rechaza credenciales inválidas con estado **401 Unauthorized**.

Endpoint probado:

```http
POST /api/v1/sessions/supervisor
```

###### Integration Test Record 02

Se ejecutó una prueba de integración sobre el endpoint **PATCH /api/v1/users/me/password**, perteneciente al módulo IAM. El objetivo fue validar el flujo de cambio obligatorio de contraseña para usuarios que ingresan con credenciales temporales.

Este test se relaciona con la **User Story US41**.

Comportamiento validado:

- El endpoint valida la contraseña temporal actual.
- El sistema rechaza contraseñas nuevas que no cumplen los requisitos de seguridad.
- El sistema actualiza el estado del usuario cuando la contraseña fue cambiada correctamente.
- El usuario queda habilitado para acceder a las funciones operativas.

Endpoint probado:

```http
PATCH /api/v1/users/me/password
```

###### Integration Test Record 03

Se ejecutó una prueba de integración sobre el endpoint **POST /api/v1/driver-sessions/{sessionId}/close**, perteneciente al módulo de operaciones. El objetivo fue validar el cierre de sesión del conductor y la liberación del vehículo asignado.

Este test se relaciona con la **User Story US42**.

Comportamiento validado:

- El endpoint permite cerrar la sesión cuando el vehículo está detenido.
- El sistema bloquea el cierre si el vehículo reporta movimiento.
- El vehículo queda disponible después del cierre exitoso.
- Se registra la hora de fin de la operación.

Endpoint probado:

```http
POST /api/v1/driver-sessions/{sessionId}/close
```

###### Integration Test Record 04

Se ejecutó una prueba de integración sobre el endpoint **GET /api/v1/drivers/{driverId}/performance**, perteneciente al módulo de analíticas. El objetivo fue validar la consulta del desempeño histórico del conductor.

Este test se relaciona con las **User Stories US04** y **US23**.

Comportamiento validado:

- El endpoint retorna métricas asociadas al conductor solicitado.
- El sistema incluye información de alertas, incidentes y cumplimiento de acciones.
- El sistema retorna una respuesta vacía o informativa cuando el conductor no tiene historial suficiente.
- La clasificación de comportamiento se calcula a partir de los eventos existentes.

Endpoint probado:

```http
GET /api/v1/drivers/{driverId}/performance
```

---

##### BDD Tests

###### BDD Test Record 01

Se implementó el Acceptance Test bajo enfoque BDD **supervisor_session_security.feature** con el objetivo de validar el acceso del supervisor al centro de control y el cambio obligatorio de contraseña temporal en el primer ingreso.

Este test se relaciona con las **User Stories US31** y **US41**.

Ruta del archivo feature:

```plaintext
src/test/resources/features/supervisor_session_security.feature
```

Ruta del archivo steps:

```plaintext
src/test/java/com/mineguard/platform/iam/bdd/SupervisorSessionSecuritySteps.java
```

```gherkin
Feature: Supervisor session security

  As a MineGuard supervisor
  I want to access the control center with valid credentials
  So that I can monitor and manage the mining operation securely

  Scenario: Supervisor accesses the control center with valid credentials
    Given a supervisor account exists with valid credentials
    When I send a POST request to "/api/v1/sessions/supervisor" with valid credentials
    Then the response status should be 200
    And the response body should contain a session token
    And the supervisor should be allowed to access the control center

  Scenario: Supervisor must change temporary password on first login
    Given a supervisor account exists with a temporary password
    When I authenticate using the temporary password
    Then the response status should be 200
    And the response body should indicate that password change is required
    When I send a PATCH request to "/api/v1/users/me/password" with a valid new password
    Then the response status should be 200
    And the account should be marked as password updated
```

![bdd-test-01](../report/assets/evidence-sprint3/testing/bdd-01-supervisor-session-security.png)

###### BDD Test Record 02

Se implementó el Acceptance Test bajo enfoque BDD **driver_shift_closure.feature** con el objetivo de validar el cierre de sesión del conductor y la desvinculación del vehículo asignado.

Este test se relaciona con la **User Story US42**.

Ruta del archivo feature:

```plaintext
src/test/resources/features/driver_shift_closure.feature
```

Ruta del archivo steps:

```plaintext
src/test/java/com/mineguard/platform/operations/bdd/DriverShiftClosureSteps.java
```

```gherkin
Feature: Driver shift closure

  As a MineGuard driver
  I want to close my session when my workday ends
  So that I can be legally disconnected from the assigned vehicle

  Scenario: Driver closes session after vehicle has stopped
    Given a driver has an active session with an assigned vehicle
    And the vehicle reports stopped status
    When I send a POST request to "/api/v1/driver-sessions/current/close"
    Then the response status should be 200
    And the session should store the operation end time
    And the vehicle should be available for other drivers

  Scenario: Driver cannot close session while vehicle is moving
    Given a driver has an active session with an assigned vehicle
    And the vehicle reports movement
    When I send a POST request to "/api/v1/driver-sessions/current/close"
    Then the response status should be 409
    And the response body should indicate that the vehicle must stop before logout
```

![bdd-test-02](../report/assets/evidence-sprint3/testing/bdd-02-driver-shift-closure.png)

###### BDD Test Record 03

Se implementó el Acceptance Test bajo enfoque BDD **alert_recommendations_and_compliance.feature** con el objetivo de validar la generación de recomendaciones de seguridad y la confirmación de acciones del conductor ante alertas.

Este test se relaciona con las **User Stories US21** y **US22**.

Ruta del archivo feature:

```plaintext
src/test/resources/features/alert_recommendations_and_compliance.feature
```

Ruta del archivo steps:

```plaintext
src/test/java/com/mineguard/platform/monitoring/bdd/AlertRecommendationsAndComplianceSteps.java
```

```gherkin
Feature: Alert recommendations and driver compliance

  As a MineGuard driver
  I want to receive clear recommendations after an alert
  So that I can react correctly during the operation

  Scenario: Driver receives a critical recommendation after a collision alert
    Given a critical collision alert exists for an active driver
    When the system processes the alert recommendation
    Then the recommendation should indicate immediate stop
    And the recommendation should be associated with the alert event

  Scenario: Supervisor sees compliance registered after driver response
    Given a critical alert required the driver to stop
    And the vehicle telemetry reports stopped status after the alert
    When the system evaluates driver compliance
    Then the alert action should be marked as fulfilled
    And the compliance result should be visible to the supervisor
```

![bdd-test-03](../report/assets/evidence-sprint3/testing/bdd-03-alert-recommendations.png)

###### BDD Test Record 04

Se implementó el Acceptance Test bajo enfoque BDD **driver_behavior_follow_up.feature** con el objetivo de validar la consulta de desempeño del conductor y el seguimiento de comportamiento por parte del supervisor.

Este test se relaciona con las **User Stories US04** y **US23**.

Ruta del archivo feature:

```plaintext
src/test/resources/features/driver_behavior_follow_up.feature
```

Ruta del archivo steps:

```plaintext
src/test/java/com/mineguard/platform/analytics/bdd/DriverBehaviorFollowUpSteps.java
```

```gherkin
Feature: Driver behavior follow up

  As a MineGuard supervisor
  I want to evaluate driver behavior
  So that I can identify risky driving patterns and take preventive actions

  Scenario: Supervisor reviews risk classification of a driver
    Given a driver has historical alerts and compliance records
    When I send a GET request to "/api/v1/drivers/DRV-001/performance"
    Then the response status should be 200
    And the response body should include alert metrics
    And the response body should include a behavior classification

  Scenario: Driver checks own historical performance
    Given an authenticated driver has previous operational events
    When the driver opens the performance view
    Then the system should display alerts, incidents and fulfilled actions
    And the information should correspond only to the authenticated driver
```

![bdd-test-04](../report/assets/evidence-sprint3/testing/bdd-04-driver-behavior.png)



#### 6.2.3.6. Execution Evidence for Sprint Review

Durante el Sprint 3 del proyecto MineGuard, el equipo completó las funcionalidades pendientes del Product Backlog, consolidando una versión funcional de la solución orientada a la prevención de accidentes en operaciones mineras. Las actividades de desarrollo estuvieron enfocadas en fortalecer los mecanismos de autenticación y seguridad, implementar el cierre de sesión y desvinculación del vehículo, habilitar la comunicación entre supervisor y conductor, incorporar recomendaciones inteligentes frente a eventos de riesgo, validar el cumplimiento de las acciones realizadas por el conductor y desarrollar funcionalidades para el análisis de desempeño y comportamiento durante la operación. Asimismo, se completaron las mejoras de la Landing Page dirigidas al segmento de operadores y conductores, fortaleciendo la presentación de las herramientas de seguridad personal ofrecidas por la plataforma.

A continuación, se presentan las principales evidencias de ejecución correspondientes a las funcionalidades implementadas durante este Sprint. Cada captura refleja una de las características desarrolladas y demuestra el comportamiento esperado de la solución en los diferentes componentes del ecosistema MineGuard.

+ Pantalla Login del Supervisor:

  La figura muestra la interfaz de autenticación del supervisor, permitiendo el acceso seguro al centro de monitoreo mediante credenciales registradas. Esta funcionalidad corresponde a la implementación de la US31 – Inicio de sesión del supervisor.

+ Pantalla donde obliga a cambiar la contraseña:

  La figura presenta el flujo de actualización obligatoria de contraseña durante el primer acceso al sistema. Esta funcionalidad garantiza que las credenciales temporales sean reemplazadas por una contraseña segura antes de habilitar el acceso a las funcionalidades operativas (US41)

+ Cierre de sesión y desvinculación del vehículo:

  La figura muestra el proceso mediante el cual el conductor finaliza su jornada de trabajo, cerrando su sesión y desvinculándose del vehículo asignado. Esta funcionalidad asegura la correcta trazabilidad de las operaciones realizadas (US42).

+ Comunicación entre supervisor y conductor:

  La figura evidencia la funcionalidad de comunicación entre supervisor y conductor después de generarse una alerta operacional, permitiendo coordinar acciones inmediatas para reducir riesgos (US11).



#### 6.2.3.7. Services Documentation Evidence for Sprint Review


#### 6.2.3.8. Software Deployment Evidence for Sprint Review

Durante el Sprint 3 del proyecto MineGuard, se consolidó la evidencia de despliegue de los principales artefactos de software desarrollados durante la iteración. El objetivo de esta sección es mostrar que los componentes del producto se encuentran disponibles en entornos de ejecución o publicación, permitiendo validar las funcionalidades finales relacionadas con seguridad de acceso, gestión de sesiones, comunicación operativa, análisis del comportamiento del conductor, recomendaciones de seguridad y experiencia informativa para operadores.

A diferencia de los sprints anteriores, este Sprint se enfocó en verificar la disponibilidad de los artefactos finales del ecosistema MineGuard, incluyendo la Landing Page, la Web Application, el Web Service, la Mobile Application, el Edge Service y los componentes asociados al prototipo IoT. Estos despliegues permiten demostrar la integración de los módulos funcionales y técnicos desarrollados durante el proyecto.

| Artifact | Deployment Status | URL / Environment |
|---|---|---|
| Landing Page | Desplegado | https://1asi0572-2610-6779-vertex.github.io/mineguard-website/ |
| Web Application | Desplegado | https://mineguard-iot.netlify.app/ |
| Web Service | Preparado para ejecución/publicación | https://mineguard-webservice.onrender.com/swagger-ui/index.html# |
| Mobile Application | Preparado para ejecución local / build móvil | Flutter local environment / Android emulator |
| Edge Service | Preparado para ejecución local / integración con backend | Local environment / Edge Service API |
| Embedded Application | Preparado para validación en entorno embebido | ESP32 / Wokwi simulation environment |
| Prototype | Preparado para validación funcional del prototipo | Wokwi simulation / physical prototype environment |



#### 6.2.3.9. Team Collaboration Insights during Sprint

+ **Web Site:**

![website-insight](../report/assets/insights-sprint2/website-i.png)

+ **Web App:**

![webapp-insight](../report/assets/insights-sprint2/webapp-i.png)

+ **Web Service:**

![webservice-insight](../report/assets/insights-sprint2/webservices-i.png)

+ **Mobile App:**

![mobile-insight](../report/assets/insights-sprint2/mobile-i.png)

+ **Edge Service:**

![webservice-insight](../report/assets/insights-sprint2/edgeservice-i.png)

+ **Embedded App:**

![webservice-insight](../report/assets/insights-sprint2/embeddedapp-i.png)

