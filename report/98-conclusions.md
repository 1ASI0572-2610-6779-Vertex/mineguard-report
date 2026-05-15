# Conclusiones

## Conclusiones AV1 (Capítulos 1 al 4)

### Conclusión general

El desarrollo del Avance 1 permitió consolidar las bases conceptuales, estratégicas y técnicas del proyecto MineGuard, una solución IoT de la startup Vertex orientada a la prevención de colisiones entre vehículos livianos y flotas autónomas en operaciones mineras de tajo abierto. A través de un proceso estructurado de análisis del problema, investigación con usuarios, modelado del dominio y diseño arquitectónico, se logró transformar una problemática crítica del sector minero peruano —que combina pérdidas humanas, paralización operativa y sanciones regulatorias de hasta 300 UIT— en una propuesta de producto técnicamente viable y centrada en el usuario.

### Conclusiones específicas

* **Sobre el Capítulo 1 (Introducción):** La caracterización de Vertex como startup y el planteamiento del problema mediante la metodología 5W2H evidenciaron la magnitud económica y humana del riesgo de colisión en minería de tajo abierto, justificando la pertinencia de una solución basada en IoT. El proceso Lean UX permitió formular hipótesis verificables sobre las necesidades de detección en tiempo real, alertas inmediatas y diferenciación de niveles de riesgo, alineando la propuesta de valor con dos segmentos objetivos claramente delimitados: la supervisión corporativa y los conductores de vehículos livianos.

* **Sobre el Capítulo 2 (Requirements Elicitation y Needfinding):** El análisis competitivo, las entrevistas y la elaboración de User Personas, User Task Matrix, Journey Maps y Empathy Maps permitieron evidenciar puntos de dolor concretos en ambos segmentos, particularmente la dependencia del factor humano, los puntos ciegos en la maquinaria pesada y la latencia inherente a la comunicación por radio. El Big Picture EventStorming consolidó esta investigación en una visión integral del dominio, identificando los eventos críticos del flujo operativo que debían ser cubiertos por el sistema.

* **Sobre el Capítulo 3 (Requirements Specification):** La definición del Ubiquitous Language, las User Stories, el Impact Mapping y el Product Backlog establecieron una base trazable entre las necesidades detectadas en el needfinding y los entregables técnicos del producto. Esta trazabilidad garantiza que cada funcionalidad propuesta responda a un dolor verificado de los usuarios y no a supuestos no validados del equipo.

* **Sobre el Capítulo 4 (Solution Software Design):** La aplicación de Domain-Driven Design en sus niveles estratégico y táctico permitió descomponer la solución en siete bounded contexts coherentes: Identity and Access Management, Service Execution and Monitoring, Profile and Preferences Management, Dashboards and Analytics, Subscriptions and Payment Management, Service Design and Planning y Resource and Asset Management. El Context Mapping definió las relaciones entre estos contextos, y el modelado con diagramas C4 (Landscape, Context, Container y Deployment) consolidó una arquitectura de software preparada para escalar y ser implementada por el equipo de desarrollo.

* **Aprendizajes del equipo:** El trabajo colaborativo en herramientas como Miro, UXPressia y Figma demostró la importancia de los procesos iterativos y de la documentación viva. La aplicación rigurosa de Lean UX y DDD permitió al equipo evitar el riesgo de construir una solución técnicamente correcta pero desconectada de las necesidades reales del sector minero.

---

## Conclusiones TB1 (Capítulos 5 al 6)

### Conclusión general

El desarrollo del Trabajo Parcial permitió materializar la propuesta conceptual y arquitectónica de MineGuard en una experiencia de usuario tangible y un entorno de implementación funcional. A través de la definición de lineamientos visuales, una arquitectura de información clara y la configuración de un ecosistema completo de herramientas de desarrollo y despliegue, se logró transitar de un diseño abstracto del dominio a un producto digital operable, sentando las bases para la validación posterior con usuarios reales del sector minero.

### Conclusiones específicas

* **Sobre los Style Guidelines (Sección 5.1):** La definición de la identidad visual de MineGuard —centrada en una paleta compuesta por azul `#2876E9`, amarillo `#ECB014`, blanco y negro `#131313`, junto con la tipografía Poppins en sus variantes Bold 700 y Regular 400— responde directamente al contexto operacional minero. El uso del amarillo inspirado en los estándares de alta visibilidad (Hi-Vis), el fondo oscuro para reducir la fatiga visual en pantallas de monitoreo continuo y el énfasis tipográfico en alertas críticas demuestran que cada decisión visual está fundamentada en las condiciones reales del entorno donde será utilizado el producto, ya sea en salas de control, cabinas de equipo pesado o dispositivos IoT embarcados.

* **Sobre la Information Architecture (Sección 5.2):** La aplicación combinada de esquemas de organización jerárquico, secuencial y matricial, junto con esquemas de categorización cronológico, alfabético, temático, por audiencia y geográfico, permitió estructurar la información del sistema de manera coherente con los flujos reales de trabajo de los tres roles identificados: Supervisor, Administrador y Conductor. El sistema de etiquetado (Centro de Control, Mapa en Vivo, Gestión de Alertas, Flota y Conductores, Reportes y Analítica, entre otros) prioriza la lectura rápida y la precisión operacional, atributos críticos en escenarios donde la velocidad de interpretación impacta directamente la seguridad.

* **Sobre los sistemas de SEO, búsqueda y navegación:** La adaptación del producto a tres canales —Landing Page, Web Application y Mobile App— con sistemas de búsqueda y navegación específicos para cada uno garantiza que tanto los visitantes potenciales como los usuarios operativos encuentren la información que necesitan sin fricciones. La elección de una sidebar contextual para supervisores y una barra inferior con accesos rápidos para conductores evidencia un diseño orientado a las metas reales de cada perfil de usuario.

* **Sobre el Software Configuration Management (Capítulo 6):** La configuración del entorno de desarrollo —que articula Jira y Trello para gestión, Figma y UXPressia para diseño, Visual Studio Code e IntelliJ IDEA como entornos de codificación, Angular como framework frontend, GitHub como sistema de control de versiones y Netlify como plataforma de despliegue continuo— consolida un flujo de trabajo profesional y reproducible. Esta configuración permite al equipo iterar rápidamente, mantener trazabilidad sobre los cambios y entregar versiones desplegadas para futuras validaciones.

* **Sobre el alcance del despliegue actual:** El despliegue inicial se concentra en la aplicación web frontend, mientras que los Web Services, la Base de Datos, la Mobile Application y la Embedded Application quedan planificados para iteraciones posteriores. Esta priorización es coherente con el enfoque incremental del proyecto y permite enfocar la validación temprana en la experiencia de los supervisores de operación, sin comprometer la coherencia de la arquitectura global definida en el Avance 1.

### Recomendaciones para próximas iteraciones

* Avanzar con el despliegue de los Web Services y la base de datos en la nube para habilitar la integración completa de la aplicación web con datos reales.
* Iniciar el desarrollo de la Mobile App y la Embedded Application, asegurando la coherencia visual y de navegación definida en la Sección 5.1 y 5.2.
* Ejecutar pruebas de usabilidad con usuarios reales del sector minero (supervisores y conductores) para validar las decisiones de arquitectura de la información tomadas en este avance.
* Establecer métricas operativas iniciales (latencia de alerta, precisión de detección, tiempo de respuesta del supervisor) que sirvan como línea base para futuras iteraciones del producto.
