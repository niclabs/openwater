# 📦 Carcasa sumergible

### Prototipado y pruebas

A continuación se presentan los detalles sobre el diseño y construcción de la carcasa sumergible del sistema en su versión actual. Se han realizado pruebas en ambiente controlado (laboratorio) sumergiendo la carcasa en tanques de agua por diferentes períodos de tiempo y evaluando efectividad en la protección del interior de acuerdo al grado de protección IP alcanzado (norma internacional CEI 60529 Degrees of Protection).

Se fabricó un primer prototipo para realizar pruebas con los sensores de presión (nivel de agua) para sumergirlos en un pozo de unos ~5 metros. Se usaron materiales de plomería genéricos y se rellenó con arroz para absorver la humedad en caso de filtraciones.

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_primera_version_2.png" width="200px">
<img title="a title" alt="Alt text" src="images/carcasa_primera_version.jpeg" width="300px"></p>

Este prototipo estuvo sumergido unos 45 minutos y al sacarlo si tenía bastante humedad dentro, pero no tenía un "pozo de agua", la humedad si era suficiente para que en el tiempo dañara la electrónica. Se cree que las filtraciones fueron por las tapas de los sensores de presión.xzx

Se diseña una nueva versión de la carcasa, ahora sumando los requerimientos de priorizar materiales accesibles y disponibles en el mercado local. La geometría inicial contempla un tubo de acrílico transparente, tapas y un soporte interno para la electrónica, además de espacios laterales para la salida de los sensores y cable UTP. Las tapas laterales realizan el sello total del dispositivo en esta versión, mediante o'rings y fijándose al soporte interno que es lo que mantendrá las tapas a presión dentro del sistema generando la protección deseada IP69.


<p align="center"><img title="a title" alt="Alt text" src="images/Nodo completo.JPG" width="600px"></p>


Se realizan diferentes pruebas del nuevo prototipo, tanto a los componentes de sello de los sensores como al equipo completo en un ambiente controlado compuesto de un tubo de pvc de 6 metros de alto para simular la presión de una columna de agua.

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_prototipo_1.jpg" width="300px"></p>

Finalmente, y luego de algunas iteraciones se logro un sistema sin filtraciones como observado en la foto de abajo :).

Se prueba este ptototipo luego en un pozo en el sector de Laguna Caren, aquí se realizaron pruebas sumergiendolo a mayores profundidades progresivamente (10, 20, 30 y 40mt).

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_validacion_1.jpg" width="300px"></p>

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_validacion_2.jpg" width="300px"></p>

<!--
Hubo diferentes resultados, positivos donde carcasa permanecio sumergida sin filtraciones y otros donde ocurrieron filtraciones. Se observan algunos casos de carcasa con filtraciones más abajo.
-->

Lo resultados fueron positivos y el sellado fue un éxito logrando una protección IP68. Hay leves filtraciones que se están revisando luego de un tiempo prolongado dependiendo de como se tape la carcasa por lo que no se clasifica aún como ip69.

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_validacion_3.jpg" width="300px"></p>

### Cable de Comunicación

Además de la carcasa, se diseño el cable de comunicación entre el módulo de captura de datos bajo el agua y el módulo de comunicación en la superficie. Para ello se utiliza un cable UTP dentro de una manguera para evitar su corrosión. El foco fue lograr un bajo costo lo que se logró con éxito costando menos de la mitad que versiones comerciales. Este cable es el encargado de transportar los datos entre el módulo de captura y el módulo de comunicación.

<p align="center">
<img title="a title" alt="Alt text" src="images/carcasa_cable_manguera.PNG" height="250px">
<img title="a title" alt="Alt text" src="images/carcasa_cable_union.PNG" height="250px">
</p>

### Resultados

El equipo, o módulo de captura de datos, una vez completamente armado tiene una forma cilindrica de un **tamaño** de 55 cm de largo y 6,3 cm de radio.

<p align="center"><img title="a title" alt="Alt text" src="images/tamaño_equipo_captura.png" width="600px"></p>

El **costo** de materiales se desprende de la carcasa y el cable de comunicación. El cable de comunicación puede variar su largo dependiendo de la aplicación, asumimos el mayor largo de 50 metros para la estimación.

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_costos.png" width="400px"></p>

Se alcanza un grado de **protección IP** IP66 pero de manera parcial, la carcasa no tiene un comportamiento confiable y está pendiente iterar sobre el diseño.

### Archivos importantes

#### Lista de Materiales e instrucciones

Más detalle sobre lista de materiales e instrucciones de armado de la carcasa se pueden encontrar en el manual de armado:

- [Manual armado carcasa v2 - 2022 Feb](https://github.com/niclabs/openwater/blob/main/3.%20Carcasa/Manual%20armado%20carcasa%20v2%20-%202022Feb.pdf)

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_listamateriales.png" width="500px"></p>


#### Diseño y fabricación

Se pueden encontrar los archivos de diseño, materiales e instrucciones en el siguiente link.

- [/niclabs/openwater/2. Carcasa](https://github.com/niclabs/openwater/tree/main/3.%20Carcasa)

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_planos_placa.png" width="220px"><img title="a title" alt="Alt text" src="images/carcasa_planos_tapa_sup.png" width="220px"><img title="a title" alt="Alt text" src="images/carcasa_planos_tapa_inf.png" width="220px"></p>

### Siguientes pasos
_\*(WIP matías)\*_
_\*TODO: agregar información sobre la manguera\*_
_\*TODO: agregar información sobre tipo de ambiente para diseñar la carcasa (requerimiento)\*_
<!--
Se puede ordenar el trabajo futuro en dos categorías dependiendo de su objetivo:

##### To Do's:

1. Disminución de costo de materiales.
2. Estandarización de proceso de fabricación.

##### To Fix:

1. Revisar mecanismo de sellado y filtraciones.

-->

<!--

- mayores dificultades, tipos de pruebas, desafíos.

Diseño final y partes


## Instrucciones armado

Manual (Adjunto)

## Resultados pruebas

Método de las pruebas

pruebas en tubo rancagua

pruebas en terreno

pruebas antes de llevar a terreno

Resumen de resultados y roadmap siguiente.

Comparación de costos cable vs cable nosotros.

- Tips
- Consejos
- Desafíos

Aprendizajes.

-->
