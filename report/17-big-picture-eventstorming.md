## 2.4. Big Picture EventStorming

En esta sección se presenta el resultado del Big Picture Event Storming realizado por el equipo, con el objetivo de comprender de manera integral el dominio del negocio asociado a la seguridad en rutas de transporte autónomo en operaciones mineras.

A través de una sesión colaborativa, se identificaron y organizaron los eventos clave que ocurren durante el flujo operativo, desde el inicio de la jornada hasta la gestión de incidentes. Este ejercicio permitió visualizar el proceso actual (As-Is), evidenciando las interacciones entre actores, las actividades críticas y los puntos donde se generan riesgos.

Como resultado, se logró identificar problemas relevantes como la detección tardía de incursiones, la dependencia del factor humano y la ausencia de sistemas de alerta en tiempo real. Asimismo, se reconocieron oportunidades de mejora orientadas a el monitoreo inteligente, que sustentan la propuesta de solución basada en IoT.

<p align="center">
    <img src="assets/big event storming.jpg" alt="upc-logo" width="1300px" height="600px"/>
</p>

Link Miro: 'https://miro.com/welcomeonboard/bFAwdEpXM0t5aFBVb0twazcxY29PZms4R2ZlZG5qZTk3OERCcnoxS0ljQS9aU25Sd3ZZaXhRN0Rid1YyU2Q5bDlyNUp4RUpSNDZHbXpiazludG1hOFNsR09IVWN3Y3p3bGg4T1lwbG5ZcGN5WlZVU0U4NEUzNFRSV3M1RWowbzB3VHhHVHd5UWtSM1BidUtUYmxycDRnPT0hdjE=?share_link_id=400051645273'


<br>

+ Events:

La imagen presenta el conjunto completo de Domain Events identificados durante la sesión de Big Picture EventStorming para el dominio de seguridad vial en minería de tajo abierto. Los eventos están representados mediante sticky notes naranjas y se distribuyen de izquierda a derecha siguiendo la línea de tiempo del proceso operativo, cubriendo desde la configuración inicial de la operación hasta el cierre del ciclo post-incidente. En total se identificaron eventos que atraviesan cinco fases del dominio: Preparación, Operación, Momento Crítico, Reacción y Post Incidente. Entre los eventos más relevantes se encuentran Ruta minera definida, Camión asignado a ruta, Vehículo menor ingresó a zona operativa, Incursión en ruta autónoma ocurrida, Riesgo de colisión generado, Colisión evitada, Colisión ocurrida, Incidente reportado, Reporte de seguridad generado y Medidas correctivas definidas. 

<p align="center">
    <img src="assets/events.jpg" alt="upc-logo" width="900px" height="500px"/>
</p>

<br>

+ Fase 1 Preparación: 

Modela el conjunto de eventos que ocurren antes del inicio de la jornada operativa. El actor principal identificado es el Supervisor de Operaciones (sticky amarillo), quien es responsable de definir y validar las rutas mineras, establecer el flujo de tránsito y asignar los vehículos a sus recorridos correspondientes. La secuencia de eventos inicia con Ruta minera definida, continúa con Ruta operativa validada, Flujo de tránsito establecido, Vehículo menor asignado a ruta y Camión asignado a ruta, hasta culminar con Jornada operativa iniciada. En verde se identifican las oportunidades de mejora: Incorporar identificación temprana de zonas críticas (aparece duplicada, lo que refuerza su prioridad). En rosa se registra la pain point central de esta fase: No existe monitoreo preventivo, evidenciando que en el proceso As-Is la preparación no contempla ningún mecanismo de detección anticipada de riesgos. 

<p align="center">
    <img src="assets/fase 1 - preparación.jpg" alt="upc-logo" width="800px" height="400px"/>
</p>

<br>

+ Fase 2 Operación: 

 Captura los eventos que ocurren durante el desplazamiento activo de vehículos en las rutas mineras. Participan dos actores: el Conductor de vehículo liviano y el Conductor de camión autónomo. La secuencia de eventos incluye Vehículo menor ingresó a zona operativa, Vehículo menor se desplazó por ruta, Camión autónomo inició recorrido y Camión autónomo circuló en ruta, hasta alcanzar los eventos de mayor riesgo: Vehículo menor se aproximó a zona restringida y Camión se aproximó a cruce crítico. En verde se registran dos oportunidades clave del sistema MineGuard: Generar alertas antes de ingresar a zonas restringidas y Mejorar visibilidad del entorno en tiempo real. En rosa se identifican los tres pain points estructurales de esta fase: Falta de visibilidad en tiempo real del entorno y Los conductores dependen únicamente de su percepción, que sintetizan la problemática central que el sistema busca resolver.

<p align="center">
    <img src="assets/fase 2 - operación.jpg" alt="upc-logo" width="800px" height="400px"/>
</p>

<br>

+ Fase 3 Momento Crítico: 

Representa el punto de mayor tensión del dominio, donde se concentra el riesgo de colisión. Los actores involucrados son el Conductor de vehículo liviano y el Conductor de camión autónomo. La cadena de eventos comienza con Vehículo menor ingresó a ruta restringida, seguido de Incursión en ruta autónoma ocurrida, Incursión no autorizada detectada (marcado en rojo por ser un evento pivotal de cambio de contexto) y Riesgo de colisión generado, hasta llegar a Distancia crítica entre vehículos alcanzada y Tiempo de reacción insuficiente identificado. En verde aparece la oportunidad central del producto: Emitir alertas tempranas en tiempo real, que corresponde directamente a la feature hypothesis H2 del Lean UX.

<p align="center">
    <img src="assets/fase 3 - momento crítico.jpg" alt="upc-logo" width="800px" height="400px"/>
</p>

<br>

+ Fase 4 Reacción: 

Modela los eventos que ocurren inmediatamente después de detectado el riesgo de colisión, con dos posibles resultados. Los actores son el Conductor de vehículo liviano y el Conductor de camión autónomo. La secuencia inicia con Operador detectó el riesgo visualmente, seguido de Velocidad reducida manualmente, Vehículo detenido de emergencia y Maniobra evasiva ejecutada. El resultado se bifurca en dos eventos de resultado: Colisión evitada o Colisión ocurrida, representando los dos desenlaces posibles del dominio. En verde aparece la oportunidad de MineGuard: Prevenir estos incidentes con rutas en tiempo real y alertando al conductor mucho antes de visualizar la incidencia, que articula la propuesta de valor del producto. En rosa se registran tres pain points que justifican la solución: Comunicación por radio realizada, Dependencia total del factor humano y El tiempo de reacción es limitado; adicionalmente, en rosa más intenso: La comunicación por radio puede ser tardía e ineficiente. 

<p align="center">
    <img src="assets/fase 4 - reaccción.jpg" alt="upc-logo" width="800px" height="400px"/>
</p>

<br>

+ Fase 5 Post Incidente: 

Captura el ciclo de cierre y aprendizaje tras un evento de riesgo o colisión. El único actor en esta fase es el Supervisor de Operaciones, lo que evidencia que la gestión post-incidente recae íntegramente en el rol de supervisión. La cadena de eventos es secuencial y lineal: Incidente reportado → Incidente registrado manualmente → Incidente clasificado → Reporte de seguridad generado → Análisis de incidente realizado → Medidas correctivas definidas. La ausencia de pain points en esta fase a diferencia de las anteriores refleja que el proceso post-incidente existe, pero opera de forma manual y tardía, sin integración con los sistemas de monitoreo en tiempo real. Esta fase se mapea al bounded context de Dashboards and Analytics, responsable de la generación de reportes, análisis de tendencias y trazabilidad de eventos críticos.

<p align="center">
    <img src="assets/fase 5 - post incidente.jpg" alt="upc-logo" width="800px" height="400px"/>
</p>

<br>


