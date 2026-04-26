## 4.2.3. Bounded Context: Service Execution and Monitoring

Este bounded context se encarga de monitorear la ejecución de operaciones en tiempo real. Centraliza la ingesta de telemetría proveniente de los sensores IoT, la evaluación de reglas de seguridad (proximidad, colisión, fatiga) y la gestión del ciclo de vida de las alertas críticas generadas para los conductores y supervisores.

### 4.2.3.1. Domain Layer

En esta capa se definen las entidades y reglas de negocio encargadas de reaccionar en tiempo real a los eventos del campo.

>**Alert**  

| Nombre | Categoría | Descripción |
| :--- | :--- | :--- |
| Alert | Aggregate Root | Representa una alerta generada a partir del análisis de datos de sensores. Gestiona su ciclo de vida (activa, monitoreo, resuelta). |

- Atributos

| Nombre | Tipo de dato | Visibilidad | Descripción |
| :--- | :--- | :--- | :--- |
| Id | int | private | Identificador único de la alerta. |
| type | enum | private | Tipo de alerta (proximidad, fatiga, colisión). |
| severity | enum | private | Nivel de gravedad (ej. Low, Medium, High, Critical). |
| description | string | private | Detalle de la alerta. |
| status | enum | private | Estado (activa, monitoreo, resuelta). |
| createdAt | datetime | private | Fecha de creación. |
| tripId | int | private | ID del viaje u operación activa (Referencia externa). |

- Métodos

| Nombre | Tipo de dato | Visibilidad | Descripción |
| :--- | :--- | :--- | :--- |
| AutoResolve() | void | Public | Cambia el estado a 'AutoResolved' si el riesgo desaparece (ej. vehículos se separan). |
| MarkAsAttended() | void | Public | Cambia el estado a 'Attended' cuando el supervisor gestiona la alerta. |
| EscalateToIncident() | void | Public | Cambia el estado y notifica al contexto externo para crear un incidente formal. |


>**SensorReading**    


| Nombre | Categoría | Descripción |
| :--- | :--- | :--- |
| SensorReading | Entity | Representa una lectura de sensor en tiempo real. |

- Atributos

| Nombre | Tipo de dato | Visibilidad | Descripción |
| :--- | :--- | :--- | :--- |
| SensorId | int | Public | ID del hardware que emite la lectura. |
| ReadingType | string | Public | Tipo de lectura |
| Value | enum | decimal | Valor de la lectura |
| Timestamp | DateTime | Public | Momento exacto de la lectura. |

- Métodos

| Nombre | Tipo de dato | Visibilidad | Descripción |
| :--- | :--- | :--- | :--- |
| isCritical() | boolean | Public | Determina si la lectura supera umbral crítico |
| isValid() | boolean | Public | Valida que la lectura tenga valores correctos |


### 4.2.3.2. Interface Layer

Esta capa se encarga de exponer la lógica del sistema de monitoreo y gestión de alertas hacia el exterior mediante API REST Controllers y Consumers de eventos.

Sus responsabilidades incluyen:

- Recepción y procesamiento de datos provenientes de sensores.
- Validación básica de datos de entrada.
- Exposición de endpoints para la gestión y consulta de alertas.
- Manejo de respuestas y errores a nivel de API.

> Controller: AlertController

| Nombre          | Categoría  | Descripción                                                              |
| --------------- | ---------- | ------------------------------------------------------------------------ |
| AlertController | Controller | Controlador encargado de gestionar operaciones relacionadas con alertas. |

Attributes

| Nombre             | Tipo de dato       | Visibilidad | Descripción                                 |
| ------------------ | ------------------ | ----------- | ------------------------------------------- |
| _alertService      | IAlertService      | Private     | Maneja la lógica de negocio de alertas.     |
| _alertQueryService | IAlertQueryService | Private     | Maneja consultas de alertas.                |

Endpoints

| Ruta                        | Método | Descripción                                                       |
| --------------------------- | ------ | ----------------------------------------------------------------- |
| /api/v1/alerts              | GET    | Obtiene todas las alertas registradas.                           |
| /api/v1/alerts/active       | GET    | Obtiene las alertas activas.                                     |
| /api/v1/alerts/{id}         | GET    | Obtiene una alerta por su ID.                                    |
| /api/v1/alerts              | POST   | Crea una nueva alerta.                                           |
| /api/v1/alerts/{id}/resolve | PUT    | Marca una alerta como resuelta automáticamente.                  |
| /api/v1/alerts/{id}/attend  | PUT    | Marca una alerta como atendida por el supervisor.                |

> Consumer: SensorDataConsumer

| Nombre             | Categoría | Descripción                                                              |
| ------------------ | --------- | ------------------------------------------------------------------------ |
| SensorDataConsumer | Consumer  | Consume eventos de sensores en tiempo real desde un sistema de mensajería. |

Responsabilidades

- Recibir eventos de telemetría de sensores.
- Transformar datos en objetos SensorReading.

> Consumer: FatigueEventConsumer

| Nombre               | Categoría | Descripción                                                              |
| -------------------- | --------- | ------------------------------------------------------------------------ |
| FatigueEventConsumer | Consumer  | Consume eventos de detección de fatiga del conductor.                   |

Responsabilidades

- Recibir eventos de fatiga.
- Enviar datos al flujo de clasificación de alertas.
- Integrar la fatiga como evento de riesgo.

