## 2.3. Needfinding

### 2.3.1. User Personas

+ **Segmento 1: Empresas Mineras de Tajo Abierto** 

<p align="center">
    <img src="assets/Segmento 1 - Raúl Ramírez.png" alt="upc-logo" width="750px" height="900px"/>
</p>

<br>

+ **Segmento 2: Operadores y Conductores de Vehículos Livianos** 

<p align="center">
    <img src="assets/Segmento 2 - Carlos Huamán.png" alt="upc-logo" width="750px" height="900px"/>
</p>

<br>

### 2.3.2. User Task Matrix

<div align="center">
    <table>
    <thead>
        <tr>
        <th rowspan="2">Tareas</th>
        <th colspan="2">Empresas Mineras </th>
        <th colspan="2">Operadores y Conductores</th>
        </tr>
        <tr>
        <th>Frecuencia</th>
        <th>Importancia</th>
        <th>Frecuencia</th>
        <th>Importancia</th>
        </tr>
    </thead>
    <tbody>
        <tr>
        <td>Monitorear rutas de transporte interno</td>
        <td>Alta</td>
        <td>Alta</td>
        <td>Baja</td>
        <td>Media</td>
        </tr>
        <tr>
        <td>Identificar zonas de riesgo</td>
        <td>Media</td>
        <td>Baja</td>
        <td>Alta</td>
        <td>Media</td>
        </tr>
        <tr>
        <td>Detectar posibles incursiones en rutas</td>
        <td>Media</td>
        <td>Alta</td>
        <td>Baja</td>
        <td>Alta</td>
        </tr>
        <tr>
        <td>Reaccionar ante situaciones de peligro</td>
        <td>Alta</td>
        <td>Alta</td>
        <td>Alta</td>
        <td>Alta</td>
        </tr>
        <tr>
        <td>Coordinar acciones ante incidentes</td>
        <td>Media</td>
        <td>Alta</td>
        <td>Baja</td>
        <td>Media</td>
        </tr>
        <tr>
        <td>Conducir respetando rutas establecidas</td>
        <td>Baja</td>
        <td>Media</td>
        <td>Alta</td>
        <td>Alta</td>
        </tr>
        <tr>
        <td>Evitar ingresar a rutas restringidas</td>
        <td>Baja</td>
        <td>Alta</td>
        <td>Alta</td>
        <td>Alta</td>
        </tr>
        <tr>
        <td>Mantener atención al entorno durante el desplazamiento</td>
        <td>Baja</td>
        <td>Alta</td>
        <td>Alta</td>
        <td>Alta</td>
        </tr>
        <tr>
        <td>Cumplir protocolos de seguridad</td>
        <td>Media</td>
        <td>Alta</td>
        <td>Alta</td>
        <td>Alta</td>
        </tr>
        <tr>
        <td>Reportar incidentes o situaciones de riesgo</td>
        <td>Media</td>
        <td>Media</td>
        <td>Media</td>
        <td>Media</td>
        </tr>
    </tbody>
    </table>
</div>

<br>

#### Análisis de la Matriz

Al observar las tareas que realizan los supervisores de operaciones mineras y los conductores de vehículos livianos en su entorno natural, sin una solución IoT especializada, se identifican los siguientes puntos clave:

+ Tareas con mayor carga (Frecuencia e Importancia):

    + Para las empresas mineras, las tareas más críticas son el monitoreo constante de rutas, la reacción ante situaciones de peligro y el cumplimiento de protocolos de seguridad. Estas actividades son esenciales para garantizar la continuidad operativa y prevenir incidentes graves.

    + Para los conductores, las tareas más relevantes son conducir respetando rutas establecidas, mantener atención constante al entorno y reaccionar ante peligros. Estas tareas son altamente frecuentes debido a su exposición directa a riesgos en campo.

+ Principales Contradicciones:

    + Las tareas de las empresas mineras son estratégicas y de supervisión (monitorear, coordinar, analizar riesgos).

    + Las tareas de los conductores son operativas y de ejecución (conducir, reaccionar, mantenerse alerta).

    + Mientras las empresas buscan control y visibilidad global, los conductores necesitan respuestas inmediatas sin distracción.

+ Principales Coincidencias:

    + Ambos segmentos coinciden en la alta importancia de reaccionar ante situaciones de peligro.

    + Ambos consideran fundamental el cumplimiento de protocolos de seguridad para evitar accidentes.

    + Existe una alineación clara en la prioridad de prevenir incidentes antes de que ocurran.

+ Puntos de Dolor Identificados:

La matriz revela que el proceso actual depende en gran medida de la observación humana y la reacción tardía. Tareas como monitorear rutas o mantenerse alerta durante la conducción son críticas pero limitadas por factores humanos como el tiempo de reacción y la visibilidad. Esta situación genera riesgos constantes y evidencia la falta de sistemas inteligentes de alerta temprana, brecha que MineGuard busca cerrar mediante la automatización y el monitoreo en tiempo real.

<br>

### 2.3.3. User Journey Mapping

+ **Segmento 1: Empresas Mineras de Tajo Abierto** 

Este User Journey Map representa la experiencia actual de un supervisor de operaciones mineras durante el monitoreo y control de rutas de transporte interno en una operación de tajo abierto. El journey ilustra el recorrido completo del usuario, desde la supervisión general de la operación y la coordinación del tránsito vehicular, hasta la respuesta ante incidentes, el análisis posterior de eventos y la definición de acciones de mejora. Este mapa permite evidenciar las limitaciones del proceso actual, caracterizado por una alta dependencia de la observación humana, reportes tardíos y baja visibilidad en tiempo real de las incursiones en rutas críticas.

<p align="center">
    <img src="assets/journey map 1.png" alt="upc-logo" width="1200px" height="750px"/>
</p>

<br>

+ **Segmento 2: Operadores y Conductores de Vehículos Livianos** 

Este User Journey Map representa la experiencia de un conductor de vehículo liviano dentro de una operación minera de tajo abierto. El journey describe el recorrido completo del usuario desde el inicio de su jornada, el desplazamiento en rutas compartidas con camiones autónomos, la interacción ante situaciones de riesgo, hasta la finalización de sus actividades. Este mapa evidencia las limitaciones actuales, donde la seguridad depende principalmente de la atención humana, la experiencia del conductor y la comunicación por radio, lo que incrementa el riesgo ante eventos imprevistos.

<p align="center">
    <img src="assets/journey map 2.png" alt="upc-logo" width="1200px" height="750px"/>
</p>

<br>

### 2.3.4. Empathy Mapping

+ **Segmento 1: Empresas Mineras de Tajo Abierto** 

<p align="center">
    <img src="assets/Empathy map 1.png" alt="upc-logo" width="850px" height="1300px"/>
</p>

<br>

+ **Segmento 2: Operadores y Conductores de Vehículos Livianos** 

<p align="center">
    <img src="assets/Empathy map 2.png" alt="upc-logo" width="850px" height="1300px"/>
</p>

