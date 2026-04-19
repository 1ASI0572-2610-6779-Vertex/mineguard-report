### 1.2.2. Lean UX Process

#### 1.2.2.1. Lean UX Problem Statement

El propósito de MineGuard es brindar a las empresas mineras una solución tecnológica preventiva que permita monitorear en tiempo real las rutas de transporte autónomo y detectar incursiones no autorizadas de vehículos menores, con el fin de reducir riesgos de colisión crítica, proteger vidas humanas y garantizar la continuidad operativa.

El problema se presenta en operaciones mineras de gran escala, donde los camiones autónomos de alto tonelaje recorren rutas internas establecidas compartiendo entorno con camionetas de supervisión, vehículos de mantenimiento y unidades de apoyo. Debido al tamaño, peso e inercia de estos vehículos autónomos, una maniobra de frenado o reacción inmediata ante un obstáculo inesperado no siempre es posible.

Hemos observado que esta situación genera riesgos constantes de accidentes graves, daños materiales de alto costo, paralización de operaciones y exposición del personal en campo. Además, evidencia una falta de sistemas inteligentes de alerta temprana que permitan anticipar invasiones de ruta y actuar antes de que ocurra una colisión. Esta brecha entre la automatización del transporte minero y la seguridad dinámica del entorno representa una necesidad crítica dentro de la industria. 

Y ante esta problemática nos surge la siguiente pregunta: ¿Cómo podríamos ayudar a las operaciones mineras a prevenir colisiones entre vehículos autónomos y unidades menores mediante una solución IoT inteligente, rápida y confiable?

+ **Domain:** Seguridad industrial minera y monitoreo inteligente de transporte autónomo.

+ **Customer Segments:** Empresas operadoras mineras de tajo abierto y compañías de infraestructura vial industrial.

+ **Pain points:**
  + Riesgo de incursión de vehículos menores en rutas autónomas
  + Tiempo de reacción limitado de camiones de alto tonelaje
  + Accidentes de alto impacto económico y humano
  + Ausencia de alertas en tiempo real

+ **Gap:** No existe una solución accesible e integrada enfocada en detectar y alertar incursiones en rutas autónomas mineras mediante sensores IoT y monitoreo en tiempo real.

+ **Vision/Strategy:** Desarrollar una plataforma IoT con sensores distribuidos y dashboard centralizado que permita detectar invasiones de ruta, emitir alertas inmediatas y mejorar la seguridad operacional minera.

+ **Initial Segment:** Operaciones mineras en Perú que utilizan flotas autónomas o semiautónomas y presentan alto tránsito de vehículos auxiliares en rutas internas.


#### 1.2.2.2. Lean UX Assumptions

##### Business Assumptions

1. **Creo nuestros usuarios tienen la necesidad** de prevenir colisiones en rutas de transporte autónomo y mejorar la seguridad operacional en tiempo real.

2. **Estas necesidades se pueden satisfacer** mediante una solución IoT con sensores distribuidos, monitoreo continuo y alertas inmediatas de incursión.

3. **Nuestros clientes iniciales serán** empresas mineras de tajo abierto en Perú que operan flotas autónomas o semiautónomas. 

4. **El valor más importante que un cliente quiere de nuestros servicios es** reducir riesgos de accidentes críticos y evitar pérdidas operativas y económicas. 

5. **El cliente también va a obtener** visibilidad en tiempo real del estado de sus rutas, datos para análisis de seguridad y mejora en la toma de decisiones. 

6. **Vamos a obtener la mayoría de los clientes mediante** alianzas con empresas mineras, demostraciones piloto (PoC) en campo y recomendaciones internas dentro del sector. 

7. **Vamos a obtener ingresos mediante** suscripción al sistema, implementación inicial del hardware IoT y servicios de mantenimiento y soporte. 

8. **Nuestra competencia en el mercado serán** sistemas de monitoreo tradicionales, soluciones de geolocalización GPS y plataformas de seguridad industrial no especializadas en rutas autónomas. 

9. **Vamos a tener ventaja frente a nuestra competencia debido a** nuestra capacidad de detección en tiempo real mediante IoT, integración Edge + Cloud y enfoque específico en incursiones de ruta. 

10. **El mayor riesgo del servicio es** la precisión y confiabilidad en la detección de incursiones en entornos mineros reales. 

11. **Lo resolveremos realizando** pruebas piloto, calibración de sensores y validación continua del sistema en condiciones simuladas y reales. 

12. **Otro riesgo que debemos considerar es que** las empresas mineras puedan resistirse a adoptar nuevas tecnologías por costos o integración con sistemas existentes.

##### User Assumptions

1. ¿Quién es el usuario? 

El usuario principal es el personal técnico y operativo de empresas mineras, incluyendo supervisores de operaciones, ingenieros de seguridad y operadores de centros de monitoreo.

2. ¿Dónde encaja nuestro producto en su vida? 

El producto se integra directamente en las actividades de monitoreo, supervisión y gestión de seguridad en rutas de transporte minero. Se convierte en una herramienta clave dentro del centro de control y en campo, apoyando la toma de decisiones en tiempo real.

3. ¿Qué problemas resuelve nuestro producto? 

Resuelve la falta de visibilidad en tiempo real sobre incursiones en rutas autónomas, reduce el riesgo de colisiones críticas, mejora el tiempo de reacción ante eventos peligrosos y disminuye pérdidas económicas y riesgos humanos asociados a accidentes.

4. ¿Cuándo y cómo se usa nuestro producto? 

Se utiliza de manera continua durante las operaciones mineras, funcionando en segundo plano mediante sensores IoT. Los usuarios interactúan a través de un dashboard, donde monitorean alertas, reciben notificaciones en tiempo real y analizan eventos registrados.

5. ¿Qué características son importantes? 

Son importantes la detección en tiempo real, alta precisión de alertas, baja latencia, confiabilidad del sistema, visualización clara de eventos y facilidad de uso del dashboard.

6. ¿Cómo debería lucir y comportarse el producto?

Debe lucir como una interfaz clara, intuitiva y profesional, con dashboards visuales simples y alertas. Debe comportarse de forma rápida, precisa y confiable, priorizando la inmediatez en la notificación y la facilidad de entender la información.

##### Feature Assumptions

+ Creemos que los usuarios necesitan visualizar en tiempo real la ubicación de los eventos de incursión en rutas mineras.

+ Creemos que los usuarios necesitan recibir alertas inmediatas cuando se detecte una invasión de ruta.

+ Creemos que los usuarios necesitan diferenciar niveles de riesgo (bajo, medio, alto) según la proximidad o velocidad del vehículo.

+ Creemos que los usuarios necesitan un historial de eventos para analizar incidentes y mejorar la seguridad.

+ Creemos que el sistema debe activar alertas físicas (luces o sonido) en los vehículos autónomos o puntos de control.

+ Creemos que el sistema debe funcionar de manera continua y automática sin intervención constante del usuario.

#### 1.2.2.3. Lean UX Hypothesis

Creemos que, si MineGuard implementa una red de sensores IoT en puntos críticos de las rutas mineras, será posible detectar incursiones de vehículos no autorizados en tiempo real, reduciendo significativamente el riesgo de colisiones con camiones autónomos.

Creemos que, si MineGuard utiliza protocolos de comunicación junto con procesamiento en el edge, las alertas generadas llegarán de manera casi inmediata tanto al vehículo autónomo como al centro de control, permitiendo una respuesta preventiva oportuna.

Creemos que, si MineGuard  un monitoreo continuo de la posición de vehículos menores, se logrará una identificación más precisa de invasiones de ruta, mejorando la confiabilidad del sistema frente a condiciones adversas del entorno minero.

Creemos que, si MineGuard presenta la información en un dashboard centralizado con visualización clara de alertas, eventos e incidencias, los operadores podrán tomar decisiones más rápidas y efectivas para mantener la continuidad operativa.

Creemos que, si MineGuard clasifica los eventos según niveles de riesgo (bajo, medio, crítico) basándose en variables como distancia, velocidad y trayectoria, se optimizará la priorización de alertas y se evitará la sobrecarga de información en los operadores.

Creemos que, si MineGuard activa alertas visuales y sonoras directamente en los camiones autónomos ante riesgos inminentes, se incrementará la capacidad de respuesta del sistema incluso en escenarios donde la intervención humana es limitada.

#### 1.2.2.4. Lean UX Canvas

