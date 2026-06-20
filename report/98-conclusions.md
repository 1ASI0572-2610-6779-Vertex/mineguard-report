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

---
## Conclusiones AV2 (Capítulos 6.2 al 6.4)

### Conclusión general

El desarrollo del Avance 2 permitió transformar MineGuard de una propuesta conceptual y un conjunto de prototipos en un ecosistema tecnológico funcional compuesto por múltiples aplicaciones y servicios interconectados. A través de la implementación de la segunda versión de la aplicación web, la primera versión de la aplicación móvil, los Web Services, el Edge Service y la Embedded Application, fue posible materializar la arquitectura IoT planteada en etapas anteriores y validar la propuesta de valor con usuarios representativos del sector minero. Los resultados obtenidos evidencian que MineGuard responde a necesidades reales relacionadas con la prevención de colisiones, la gestión de alertas y la centralización de información operacional en entornos de minería de tajo abierto.

### Conclusiones específicas

* **Sobre Sprint 2 y la implementación del ecosistema MineGuard (Sección 6.2.2)**: El Sprint 2 permitió desarrollar los principales componentes funcionales definidos dentro del alcance del proyecto. La construcción simultánea de la aplicación web, la aplicación móvil, los Web Services, el Edge Service y la Embedded Application demostró la viabilidad de implementar una arquitectura distribuida capaz de soportar los procesos de monitoreo, visualización de eventos y gestión de alertas planteados para MineGuard. Este avance representa la transición desde una etapa centrada en diseño y planificación hacia una fase de construcción e integración tecnológica.

* **Sobre la evolución de la Web Application (Sección 6.2.2.4)**: La segunda versión de la aplicación web permitió incorporar funcionalidades orientadas a supervisores y administradores de operaciones mineras, incluyendo visualización de eventos, gestión de alertas e información operativa. Esta evolución permitió acercar la solución a los flujos de trabajo reales identificados durante las entrevistas iniciales, proporcionando una plataforma más alineada con las necesidades de monitoreo y supervisión en tiempo real presentes en el entorno minero.

* **Sobre el desarrollo de la Mobile Application (Sección 6.2.2.4)**: La implementación de la primera versión de la aplicación móvil permitió extender el alcance de MineGuard hacia los conductores de vehículos livianos, incorporando mecanismos para la visualización de alertas y consulta de eventos relevantes para la seguridad operacional. Este componente constituye un paso importante dentro de la estrategia de prevención de riesgos, ya que acerca la información directamente al personal que interactúa diariamente con los peligros presentes en la operación minera.

* **Sobre la implementación de los Web Services, Edge Service y Embedded Application (Secciones 6.2.2.4 y 6.2.2.7)**: El desarrollo de los Web Services, junto con la implementación inicial del Edge Service y la Embedded Application, permitió establecer las bases técnicas necesarias para la integración de dispositivos IoT dentro de la solución. Estos componentes validan la factibilidad de la arquitectura propuesta y preparan el camino para futuras iteraciones orientadas a la captura, procesamiento y transmisión de información proveniente de sensores desplegados en campo.

* **Sobre la validación con usuarios y la evaluación heurística (Sección 6.3)**: Las entrevistas realizadas con supervisores y conductores permitieron obtener evidencia favorable respecto a la utilidad percibida de la solución. Los participantes destacaron el valor de contar con una plataforma que centralice información operativa y facilite la identificación de eventos relevantes para la seguridad. Asimismo, la evaluación heurística permitió identificar oportunidades de mejora relacionadas con la presentación de alertas, la organización de la información y la experiencia de usuario, proporcionando una base sólida para la planificación de futuras iteraciones.

## Recomendaciones para próximas iteraciones

* Integrar completamente la aplicación web, la aplicación móvil, los Web Services, el Edge Service y la Embedded Application para validar el funcionamiento integral del ecosistema MineGuard.

* Mejorar la experiencia de usuario de la plataforma web y móvil considerando los hallazgos obtenidos durante las entrevistas de validación y la evaluación heurística, especialmente en la visualización de alertas y organización de la información.

* Realizar nuevas pruebas con supervisores y conductores del sector minero para obtener una mayor cantidad de retroalimentación y validar futuras mejoras del sistema.

* Incorporar métricas operativas básicas, como tiempo de respuesta ante alertas y cantidad de eventos registrados, que permitan evaluar el desempeño de MineGuard en futuras iteraciones.


