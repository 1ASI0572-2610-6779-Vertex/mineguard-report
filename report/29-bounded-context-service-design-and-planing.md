## 4.2.5. Bounded Context: Service Design and Planning

Este bounded context se encarga de gestionar la configuración física, espacial y de recursos operativos de la mina de forma local antes de iniciar el monitoreo en tiempo real. Centraliza la importación de topografía, el trazado de geofences (zonas de riesgo), la asignación de permisos vehiculares y la vinculación de sensores IoT a la flota, garantizando un entorno parametrizado y sin puntos ciegos.

### 4.2.5.1. Domain Layer

En esta capa se definen las entidades y reglas de negocio encargadas de modelar el entorno espacial de la mina y el hardware de los recursos.

**GeofenceZone** 
| Nombre | Categoría | Descripción |
| :--- | :--- | :--- |
| GeofenceZone | Aggregate Root | Define un área geográfica delimitada en la mina con un nivel de riesgo específico y reglas de acceso. |

- Atributos

| Nombre | Tipo de dato | Visibilidad | Descripción |
| :--- | :--- | :--- | :--- |
| zoneId | UUID | private | Identificador único de la zona geográfica. |
| name | string | private | Nombre asignado a la zona. |
| type | enum | private | Clasificación del riesgo (ej. DANGER_ZONE, SAFE_ZONE). |
| status | enum | private | Estado de activación de la zona. |

- Métodos

| Nombre | Tipo de dato | Visibilidad | Descripción |
| :--- | :--- | :--- | :--- |
| addBoundaryPoint() | void | Public | Añade un punto de coordenada para trazar el polígono. |
| assignPermission() | void | Public | Crea y asocia una regla de acceso a un conductor. |
| validatePolygon() | boolean | Public | Verifica que los límites trazados no tengan errores de superposición. |


**Vehicle** 
| Nombre | Categoría | Descripción |
| :--- | :--- | :--- |
| Vehicle | Aggregate Root | Representa un vehículo físico de la flota operativa dentro del campamento minero. |

- Atributos

| Nombre | Tipo de dato | Visibilidad | Descripción |
| :--- | :--- | :--- | :--- |
| vehicleId | UUID | private | Identificador único del vehículo. |
| plateCode | string | private | Placa o código de identificación del vehículo. |
| status | enum | private | Estado operativo del recurso. |

- Métodos

| Nombre | Tipo de dato | Visibilidad | Descripción |
| :--- | :--- | :--- | :--- |
| linkSensor() | void | Public | Vincula estructuralmente un dispositivo IoT de telemetría al vehículo. |


**Sensor** 
| Nombre | Categoría | Descripción |
| :--- | :--- | :--- |
| Sensor | Entity | Representa el hardware IoT instalado en un vehículo para transmitir telemetría. |

- Atributos

| Nombre | Tipo de dato | Visibilidad | Descripción |
| :--- | :--- | :--- | :--- |
| sensorId | UUID | private | Identificador único del hardware del sensor. |
| sensorType | enum | private | Tipo de hardware (ej. GPS_TRACKER, TELEMETRY_NODE). |
| status | enum | private | Estado actual de conexión del dispositivo. |

- Métodos

| Nombre | Tipo de dato | Visibilidad | Descripción |
| :--- | :--- | :--- | :--- |
| calibrateConnection() | boolean | Public | Verifica el estado de la comunicación local del sensor. |


### 4.2.5.2. Interface Layer

Esta capa se encarga de exponer la lógica de configuración espacial y de recursos hacia el exterior mediante API REST Controllers locales.

Sus responsabilidades incluyen:
- Recepción de archivos topográficos locales y coordenadas.
- Validación básica de datos de entrada desde la interfaz de usuario (Centro de Control UI).
- Exposición de endpoints para el registro de la flota y hardware.
- Manejo de respuestas y errores en la configuración.

**Controller: ServiceDesignController**

| Nombre          | Categoría  | Descripción                                                              |
| --------------- | ---------- | ------------------------------------------------------------------------ |
| ServiceDesignController | Controller | Controlador encargado de gestionar las operaciones de diseño del entorno y recursos. |

Attributes

| Nombre             | Tipo de dato       | Visibilidad | Descripción                                 |
| ------------------ | ------------------ | ----------- | ------------------------------------------- |
| _commandService    | IServiceDesignCommandService | Private     | Maneja la lógica de negocio para la configuración de la mina. |

Endpoints

| Ruta                        | Método | Descripción                                                       |
| --------------------------- | ------ | ----------------------------------------------------------------- |
| /api/v1/sdp/map/import      | POST   | Carga un archivo topográfico local al sistema.                    |
| /api/v1/sdp/geofence/draw   | POST   | Registra las coordenadas de un nuevo polígono y define la zona.   |
| /api/v1/sdp/resources/register | POST | Registra conductores y vehículos en el padrón local.            |
| /api/v1/sdp/hardware/link-sensor | POST | Vincula un Sensor IoT a un vehículo específico.                 |


### 4.2.5.3. Application Layer

En la Application Layer se ubican los servicios que actúan como Command Handlers, encargados de coordinar el flujo de procesos de negocio relacionados con la configuración de la mina antes del despliegue operativo.

| Nombre               | Categoría                 | Descripción                                                                         |
| -------------------- | ------------------------- | ----------------------------------------------------------------------------------- |
| IServiceDesignCommandService | Command Handler Interface | Expone métodos para manejar comandos de configuración de zonas, recursos y hardware IoT. |

**Commands manejados**
- `ImportTopographyCommand` (Orquesta el flujo para procesar y guardar un archivo de mapa local).
- `DrawPolygonCommand` (Instancia el agregado GeofenceZone a partir de coordenadas y solicita su persistencia).
- `RegisterResourceCommand` (Gestiona la creación inicial de conductores y vehículos).
- `LinkSensorCommand` (Vincula un sensor a un vehículo y valida la comunicación local).


### 4.2.5.4. Infrastructure Layer

En la Infrastructure Layer se encuentran las implementaciones concretas de los repositorios definidos en la capa de dominio. Esta capa es responsable de la persistencia de datos relacionales en MySQL y de la publicación de eventos hacia el bus de mensajería local.

| Nombre                     | Categoría                 | Implementa                 | Descripción                                                                 |
| -------------------------- | ------------------------- | -------------------------- | --------------------------------------------------------------------------- |
| GeofenceRepositoryImpl     | Repository Implementation | IGeofenceRepository        | Gestiona la persistencia de las entidades GeofenceZone y ZoneBoundary en BD. |

Funcionalidad clave

- `void save(GeofenceZone zone)` → Registra una nueva zona geográfica y sus límites.
- `GeofenceZone findById(UUID zoneId)` → Busca la configuración de una zona por ID.
- `List<GeofenceZone> findAllActive()` → Obtiene todas las zonas habilitadas en la mina.


| Nombre                          | Categoría                 | Implementa                      | Descripción                                                                 |
| ------------------------------- | ------------------------- | ------------------------------- | --------------------------------------------------------------------------- |
| ResourceRepositoryImpl          | Repository Implementation | IResourceRepository             | Gestiona la persistencia de la flota operativa (Drivers, Vehicles, Sensors).|

Funcionalidad clave

- `void saveVehicle(Vehicle vehicle)` → Registra un vehículo y su sensor vinculado.
- `Vehicle findByPlateCode(string plateCode)` → Busca un vehículo específico en el padrón.


| Nombre                 | Categoría            | Implementa | Descripción                                                                 |
| ---------------------- | -------------------- | ---------- | --------------------------------------------------------------------------- |
| DatabaseContext        | Persistence Context  | -          | Contexto de base de datos que gestiona la conexión y mapeo ORM de entidades. |

Responsabilidades

- Configurar entidades (GeofenceZone, Vehicle, Sensor, ZoneBoundary, ZonePermission).
- Gestionar conexión a la base de datos MySQL local.

| Nombre                 | Categoría            | Implementa | Descripción                                                                 |
| ---------------------- | -------------------- | ---------- | --------------------------------------------------------------------------- |
| LocalEventPublisherImpl| Message Broker Impl. | IEventPublisher | Publica eventos de dominio hacia el bus de mensajería interno. |

Responsabilidades

- Publicar el evento *Configuración Desplegada* (`ConfigurationDeployedEvent`) para que el módulo de *Service Execution* inicie el monitoreo.



### 4.2.5.5. Bounded Context Software Architecture Component Level Diagrams.

En este diagrama se refleja la descomposición estructural del contenedor backend para el diseño de la mina. El bloque principal es el `ServiceDesignController`, el cual recibe solicitudes HTTP locales desde la interfaz de usuario. Este controlador orquesta las operaciones invocando a tres servicios de aplicación principales: `GeofenceService` , `ResourceManagementService` y `SensorSetupService` .

Cada servicio utiliza su respectivo repositorio para abstraer el acceso a la base de datos MySQL local, donde se consolidan las zonas de riesgo y los recursos operativos. Finalmente, se evidencia la comunicación asíncrona hacia el contexto de *Service Execution and Monitoring* mediante la publicación de event de dominio.

<img src="report\assets\ComponentDiagram_ServiceDesign.png">

### 4.2.5.6. Bounded Context Software Architecture Code Level Diagrams. 

#### 4.2.5.6.1. Bounded Context Domain Layer Class Diagrams.

El siguiente diagrama UML representa la estructura táctica del dominio. Se identifican dos agregados principales: `GeofenceZone`, que encapsula la delimitación espacial y los permisos de acceso; y `Vehicle`, que gestiona la vinculación física del hardware mediante la entidad `Sensor`. 

El diagrama detalla los atributos, métodos y el scope correspondiente para cada clase, así como la multiplicidad y dirección de las relaciones. Además, se incluye la interfaz `ServiceDesignCommandService` y los comandos que mutan el estado del dominio al configurar la mina.

<img src="report\assets\DomainClassDiagram_ServiceDesign.png">

#### 4.2.5.6.2. Bounded Context Database Design Diagram.

Este diagrama de base de datos representa el submodelo de persistencia exclusivo del bounded context Service Design and Planning. La estructura centraliza la configuración espacial a través de la tabla `GeofenceZone` y sus coordenadas en `ZoneBoundary`. 

Asimismo, gestiona la flota operativa relacionando la tabla maestra `Drivers` con `Vehicles`, y asegurando la trazabilidad del hardware al vincular cada vehículo con un `Sensor` específico. Finalmente, la tabla `ZonePermission` actúa como un componente clave para la seguridad, cruzando la autorización de un conductor con una zona geográfica determinada. Este diseño relacional garantiza que toda la configuración previa a la operación esté validada y estructurada correctamente.

<img src="report\assets\DatabaseDiagram_ServiceDesign.jpeg">
