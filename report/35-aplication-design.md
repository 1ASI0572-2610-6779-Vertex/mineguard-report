## 5.4. Applications UX/UI Design 
### 5.4.1. Applications Wireframes

La propuesta de wireframes fue desarrollada aplicando los principios de diseño inclusivo, accesibilidad, jerarquía visual y usabilidad. Se busca asegurar una navegación clara y coherente, tanto para turistas como para agencias, adaptando la estructura y contenido de la interfaz según el tipo de usuario para optimizar su experiencia.  

![Wireframe 1](../report/assets/wireframe1.png)

#### VISTA SUPERVISOR

![Wireframe 2](../report/assets/wireframe2.png)
![Wireframe 3](../report/assets/wireframe3.png)
![Wireframe 4](../report/assets/wireframe4.png)
![Wireframe 5](../report/assets/wireframe5.png)
![Wireframe 6](../report/assets/wireframe6.png)
![Wireframe 7](../report/assets/wireframe7.png)

#### VISTA ADMINISTRADOR

![Wireframe 8](../report/assets/wireframe8.png)
![Wireframe 9](../report/assets/wireframe9.png)
![Wireframe 10](../report/assets/wireframe10.png)

### 5.4.2. Applications Wireflow Diagrams

Los diagramas de wireflow ilustran las rutas de navegación y la interacción del usuario a través de las diferentes pantallas de la plataforma. Estos diagramas combinan la estructura visual de los wireframes con la lógica operativa de los diagramas de flujo, permitiendo visualizar claramente cómo los distintos roles completan sus tareas principales dentro del sistema.

#### VISTA SUPERVISOR

El siguiente diagrama detalla el flujo principal de monitoreo del Supervisor. Muestra la ruta desde el inicio de sesión hacia el Centro de Control principal, ramificándose de manera intuitiva hacia módulos críticos como el Mapa en Vivo, la Bandeja de Gestión de Alertas (Incidentes) y el panel de Reportes y Analítica.

![Wireflow 1 - Monitoreo Supervisor](../report/assets/wireflow1.png)

Este segundo diagrama se enfoca en el flujo de administración de recursos operativos por parte del Supervisor. Ilustra el recorrido desde el dashboard principal hacia la sección de Flota y Conductores, permitiendo alternar fácilmente entre el Inventario de Vehículos y el Directorio de Conductores.

![Wireflow 2 - Flota y Conductores](../report/assets/wireflow2.png)

#### VISTA ADMINISTRADOR

Para el perfil de Administrador, este diagrama describe la ruta de configuración y supervisión del sistema. Inicia con el acceso al panel de Salud Operativa y despliega las rutas hacia la Gestión de Roles (para la creación de nuevos supervisores) y hacia los registros del sistema (Auditoría y Archivo).

![Wireflow 3 - Panel de Administrador](../report/assets/wireflow3.png)
### 5.4.3. Applications Mock-ups

A continuación se presentan los mock-ups de alta fidelidad, desarrollados a partir de los wireframes previamente establecidos. En esta etapa se ha integrado la identidad visual del proyecto, aplicando la paleta de colores, tipografías y componentes gráficos definitivos. El objetivo es proporcionar una representación visual realista y detallada de la interfaz final, garantizando una experiencia de usuario (UX) intuitiva y un diseño de interfaz (UI) atractivo y funcional para los diferentes roles del sistema.

![Mockup 1](../report/assets/mockup1.png)

#### VISTA SUPERVISOR

![Mockup 2](../report/assets/mockup2.png)
![Mockup 3](../report/assets/mockup3.png)
![Mockup 4](../report/assets/mockup4.png)
![Mockup 5](../report/assets/mockup5.png)
![Mockup 6](../report/assets/mockup6.png)
![Mockup 7](../report/assets/mockup7.png)

#### VISTA ADMINISTRADOR

![Mockup 8](../report/assets/mockup8.png)
![Mockup 9](../report/assets/mockup9.png)
![Mockup 10](../report/assets/mockup10.png)

### 5.4.4. Applications User Flow Diagrams

Los diagramas de flujo de usuario (User Flows) representan visualmente el recorrido paso a paso que realiza un usuario para completar tareas específicas dentro de la plataforma. Estos diagramas destacan los puntos de decisión, las validaciones del sistema y los diferentes caminos (escenarios de éxito o error) que resultan de las interacciones, asegurando que la lógica de negocio esté correctamente mapeada.

El primer flujo fundamental es el proceso de **Autenticación y Enrutamiento**. Al iniciar sesión, el sistema evalúa las credenciales y, mediante una condicional de rol, redirige automáticamente al usuario a su entorno de trabajo correspondiente: el Centro de Control (Supervisor) o el Panel de Recursos (Administrador).

![User Flow 1 - Iniciar Sesión](../report/assets/userflow1.png)

#### VISTA SUPERVISOR

El siguiente diagrama ilustra el proceso operativo para **Agregar un Vehículo**. El supervisor navega desde el panel principal hacia el módulo de "Flota y Conductores", abre el formulario de registro y envía los datos. El flujo muestra la bifurcación del sistema: si los datos son correctos, se muestra un mensaje de éxito; de lo contrario, se solicita la corrección de la información.

![User Flow 2 - Agregar Vehículo](../report/assets/userflow2.png)

De manera homóloga a los vehículos, este diagrama detalla los pasos para **Agregar un Conductor**. El supervisor completa el formulario con los datos del personal y el sistema valida la entrada. Un registro exitoso culmina con la generación de las credenciales de acceso para el nuevo conductor.

![User Flow 3 - Agregar Conductor](../report/assets/userflow3.png)

Este flujo describe una de las tareas más críticas: **Gestionar una Alerta**. Muestra la ruta del supervisor hacia la bandeja de incidentes, la selección de una alerta específica y la decisión operativa tomada para resolverla (clasificándola como falsa alarma o marcándola como resuelta), desencadenando las notificaciones visuales correspondientes en la interfaz.

![User Flow 5 - Gestionar Alerta](../report/assets/userflow5.png)

#### VISTA ADMINISTRADOR

Para el perfil administrativo, este diagrama explica el proceso para **Agregar un Supervisor**. El administrador accede a la sección de Gestión de Usuarios y completa los datos requeridos. El flujo incluye la validación de la información; si es correcta, el sistema envía las credenciales automáticamente al nuevo supervisor y muestra un mensaje de éxito.

![User Flow 4 - Agregar Supervisor](../report/assets/userflow4.png)