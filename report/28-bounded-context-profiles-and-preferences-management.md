### 4.2.4. Bounded Context: Profiles and Preferences Management

En este bounded context se gestionan los perfiles de usuario y sus preferencias dentro de MineGuard, permitiendo personalizar la experiencia del sistema según el rol operativo, idioma, canales de notificación, alertas y rutas críticas de interés.

<br>

### 4.2.4.1. Domain Layer

En el bounded context Profiles and Preferences Management, la capa de dominio representa las reglas principales relacionadas con la gestión del perfil operativo del usuario y sus preferencias dentro de MineGuard. Esta capa permite definir cómo se organiza la información del usuario, qué preferencias puede configurar y bajo qué condiciones dichas configuraciones son válidas.

+ Entities:

| Clase | Propósito | Atributos principales | Métodos principales |
|------|----------|----------------------|--------------------|
| **UserProfile** | Representa el perfil operativo del usuario. | id, userId, fullName, email, phoneNumber, operationalRole, status | updateProfile(), deactivateProfile(), activateProfile() |
| **UserPreferences** | Agrupa las preferencias del usuario. | id, userProfileId, language, riskLevel, createdAt, updatedAt | updatePreferences(), resetToDefault() |
| **NotificationPreference** | Define canales de notificación. | id, userPreferencesId, channel, isEnabled | enableChannel(), disableChannel(), changeChannel() |
| **AlertPreference** | Define configuración de alertas. | id, userPreferencesId, visualAlert, soundAlert, riskLevelThreshold | configureAlert(), enableVisualAlert(), enableSoundAlert() |
| **CriticalRoutePreference** | Representa rutas críticas. | id, userPreferencesId, routeId, priorityLevel | assignRoute(), removeRoute(), changePriority() |

<br>

+ Value Objects:

| Clase | Propósito |
|------|----------|
| **OperationalRole** | Rol operativo del usuario. |
| **ProfileStatus** | Estado del perfil (activo/inactivo). |
| **LanguagePreference** | Idioma del usuario. |
| **RiskLevel** | Nivel de riesgo configurado. |
| **NotificationChannel** | Canal de notificación. |

<br>

+ Aggregate:

| Elemento | Descripción |
|---------|------------|
| **UserProfile (Aggregate Root)** | Centraliza la gestión del perfil y sus preferencias asociadas. |


+ Domain Services:

| Clase | Propósito |
|------|----------|
| **PreferenceValidationService** | Valida reglas de negocio de preferencias. |
| **ProfileStatusService** | Gestiona reglas de estado del perfil. |

+ Repository Interfaces:

| Clase | Propósito |
|------|----------|
| **UserProfileRepository** | Acceso a datos de perfiles. |
| **UserPreferencesRepository** | Acceso a datos de preferencias. |

<br>

### 4.2.4.2. Interface Layer

En el bounded context Profiles and Preferences Management, la capa de interfaz se encarga de exponer las operaciones necesarias para que los usuarios puedan gestionar su perfil y preferencias dentro de MineGuard. Esta capa recibe las solicitudes desde la aplicación web valida la entrada básica y delega la lógica de negocio a la capa de aplicación.

+ Clases:

    + **UserProfileController:** Expone endpoints para consultar, actualizar, activar o desactivar el perfil operativo del usuario.

    + **UserPreferencesController:** Permite consultar, configurar, actualizar o restablecer las preferencias generales del usuario.

    + **NotificationPreferencesController:** Gestiona las solicitudes relacionadas con canales de notificación y preferencias de comunicación.

    + **AlertPreferencesController:** Expone operaciones para configurar alertas visuales, sonoras y niveles de riesgo.

    + **CriticalRoutePreferencesController:** Permite seleccionar, consultar o modificar las rutas críticas asociadas a las preferencias del usuario.

<br>

**UserProfileController**

| Nombre | Método | Ruta | Descripción |
| ------ | ------ | ---- | ----------- |
| getUserProfileById | GET | /api/v1/profiles/{profileId} | Obtiene el perfil operativo de un usuario por su ID. |
| getUserProfileByUserId | GET | /api/v1/profiles/user/{userId} | Obtiene el perfil asociado a un usuario autenticado. |
| createUserProfile | POST | /api/v1/profiles | Crea un nuevo perfil operativo de usuario. |
| updateUserProfile | PUT | /api/v1/profiles/{profileId} | Actualiza los datos del perfil operativo. |
| deactivateUserProfile | PATCH | /api/v1/profiles/{profileId}/deactivate | Desactiva un perfil de usuario. |
| activateUserProfile | PATCH | /api/v1/profiles/{profileId}/activate | Activa un perfil de usuario. |

**UserPreferencesController**

| Nombre | Método | Ruta | Descripción |
| ------ | ------ | ---- | ----------- |
| getUserPreferences | GET | /api/v1/profiles/{profileId}/preferences | Obtiene las preferencias generales del usuario. |
| configureUserPreferences | POST | /api/v1/profiles/{profileId}/preferences | Configura las preferencias iniciales del usuario. |
| updateUserPreferences | PUT | /api/v1/profiles/{profileId}/preferences | Actualiza las preferencias generales del usuario. |
| resetUserPreferences | PATCH | /api/v1/profiles/{profileId}/preferences/reset | Restablece las preferencias a valores por defecto. |

**NotificationPreferencesController**

| Nombre | Método | Ruta | Descripción |
| ------ | ------ | ---- | ----------- |
| getNotificationPreferences | GET | /api/v1/profiles/{profileId}/preferences/notifications | Obtiene las preferencias de notificación del usuario. |
| updateNotificationPreferences | PUT | /api/v1/profiles/{profileId}/preferences/notifications | Actualiza los canales de notificación configurados. |
| enableNotificationChannel | PATCH | /api/v1/profiles/{profileId}/preferences/notifications/{channel}/enable | Activa un canal de notificación. |
| disableNotificationChannel | PATCH | /api/v1/profiles/{profileId}/preferences/notifications/{channel}/disable | Desactiva un canal de notificación. |

**AlertPreferencesController**

| Nombre | Método | Ruta | Descripción |
| ------ | ------ | ---- | ----------- |
| getAlertPreferences | GET | /api/v1/profiles/{profileId}/preferences/alerts | Obtiene las preferencias de alerta del usuario. |
| updateAlertPreferences | PUT | /api/v1/profiles/{profileId}/preferences/alerts | Actualiza alertas visuales, sonoras y umbral de riesgo. |
| enableVisualAlert | PATCH | /api/v1/profiles/{profileId}/preferences/alerts/visual/enable | Activa las alertas visuales. |
| enableSoundAlert | PATCH | /api/v1/profiles/{profileId}/preferences/alerts/sound/enable | Activa las alertas sonoras. |

**CriticalRoutePreferencesController**

| Nombre | Método | Ruta | Descripción |
| ------ | ------ | ---- | ----------- |
| getCriticalRoutePreferences | GET | /api/v1/profiles/{profileId}/preferences/critical-routes | Obtiene las rutas críticas seleccionadas por el usuario. |
| assignCriticalRoute | POST | /api/v1/profiles/{profileId}/preferences/critical-routes | Asigna una nueva ruta crítica al usuario. |
| updateCriticalRoutePreference | PUT | /api/v1/profiles/{profileId}/preferences/critical-routes/{routeId} | Actualiza la prioridad de una ruta crítica. |
| removeCriticalRoutePreference | DELETE | /api/v1/profiles/{profileId}/preferences/critical-routes/{routeId} | Elimina una ruta crítica de las preferencias del usuario. |

<br>

### 4.2.4.3. Application Layer

En el bounded context Profiles and Preferences Management, la capa de aplicación se encarga de coordinar los flujos de negocio relacionados con la gestión de perfiles y preferencias del usuario. Esta capa recibe comandos desde la capa de interfaz, ejecuta los casos de uso correspondientes y coordina la interacción con el dominio y los repositorios.

| Clase | Propósito |
|------|----------|
| **CreateUserProfileCommandHandler** | Gestiona el flujo para crear un perfil operativo asociado a un usuario autenticado. |
| **UpdateUserProfileCommandHandler** | Coordina la actualización de datos del perfil, como nombre, teléfono o rol operativo. |
| **DeactivateUserProfileCommandHandler** | Ejecuta el proceso para desactivar un perfil de usuario cuando ya no debe operar en el sistema. |
| **ConfigureUserPreferencesCommandHandler** | Gestiona la configuración inicial de preferencias del usuario, incluyendo idioma, alertas y rutas críticas. |
| **UpdateUserPreferencesCommandHandler** | Coordina la modificación de preferencias previamente guardadas. |
| **ResetUserPreferencesCommandHandler** | Restablece las preferencias del usuario a los valores por defecto. |
| **UserPreferencesConfiguredEventHandler** | Reacciona cuando las preferencias han sido configuradas, permitiendo actualizar vistas o notificar a otros contextos. |
| **UserProfileUpdatedEventHandler** | Reacciona ante cambios en el perfil del usuario para mantener actualizada la información utilizada por otros módulos. |

<br>

### 4.2.4.4. Infrastructure Layer

En el bounded context Profiles and Preferences Management, la capa de infraestructura se encarga de la interacción con servicios externos como la base de datos y mecanismos de mensajería. Esta capa implementa las interfaces definidas en el dominio, permitiendo la persistencia de perfiles y preferencias de usuario, así como la publicación de eventos hacia otros contextos del sistema.

+ Clases:

    + **UserProfileRepositoryImpl:** Implementa el acceso a base de datos para la entidad UserProfile.

    + **UserPreferencesRepositoryImpl:** Implementa el acceso a base de datos para la entidad UserPreferences.

    + **DatabaseConnection:** Gestiona la conexión y operaciones básicas con la base de datos.

    + **PreferencesEventPublisher:** Publica eventos como cambios en preferencias hacia otros contextos.

    + **NotificationServiceClient:** Permite la integración con servicios externos de notificación.

<br>


**UserProfileRepository**

| Método | Descripción |
|--------|------------|
| save | Guarda o actualiza un perfil de usuario. |
| findById | Busca un perfil por su identificador. |
| findByUserId | Obtiene el perfil asociado a un usuario específico. |
| update | Actualiza la información de un perfil existente. |
| deactivate | Cambia el estado del perfil a inactivo. |


**UserPreferencesRepository**

| Método | Descripción |
|--------|------------|
| save | Guarda las preferencias de usuario. |
| findById | Busca preferencias por su identificador. |
| findByUserProfileId | Obtiene las preferencias asociadas a un perfil. |
| update | Actualiza preferencias existentes. |
| resetToDefault | Restablece las preferencias a valores por defecto. |


**DatabaseConnection**

| Método | Descripción |
|--------|------------|
| connect | Establece conexión con la base de datos. |
| disconnect | Cierra la conexión. |
| executeQuery | Ejecuta consultas sobre la base de datos. |



**PreferencesEventPublisher**

| Método | Descripción |
|--------|------------|
| publishProfileUpdated | Publica eventos cuando un perfil es actualizado. |
| publishPreferencesConfigured | Publica eventos cuando se configuran preferencias. |
| publishPreferencesUpdated | Publica eventos cuando se actualizan preferencias. |


**NotificationServiceClient**

| Método | Descripción |
|--------|------------|
| sendEmail | Envía notificaciones por correo electrónico. |
| sendSMS | Envía notificaciones por SMS. |
| sendPushNotification | Envía notificaciones push al usuario. |

<br>


### 4.2.4.5. Bounded Context Software Architecture Component Level Diagram

<img src="assets/Profiles and Preferences ManagementProfilesAndPreferencesComponents-dark.png">

<br>

### 4.2.4.6. Bounded Context Software Architecture Code Level Diagrams

#### 4.2.4.6.1. Bounded Context Domain Layer Class Diagrams

<img src="assets/class diagram Profiles and Preferences Management.png">

<br>

#### 4.2.4.6.2. Bounded Context Database Design Diagram

<img src="assets/database Profiles and Preferences Management.png">

<br>





