# 馃摝 Carcasa sumergible

### Prototipado y pruebas

A continuaci贸n se presentan los detalles sobre el dise帽o y construcci贸n de la carcasa sumergible del sistema en su versi贸n actual. Se han realizado pruebas en ambiente controlado (laboratorio) sumergiendo la carcasa en tanques de agua por diferentes per铆odos de tiempo y evaluando efectividad en la protecci贸n del interior de acuerdo al grado de protecci贸n IP alcanzado (norma internacional CEI 60529 Degrees of Protection).

Se fabric贸 un primer prototipo para realizar pruebas con los sensores de presi贸n (nivel de agua) para sumergirlos en un pozo de unos ~5 metros. Se usaron materiales de plomer铆a gen茅ricos y se rellen贸 con arroz para absorver la humedad en caso de filtraciones.

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_primera_version_2.png" width="200px">
<img title="a title" alt="Alt text" src="images/carcasa_primera_version.jpeg" width="300px"></p>

Este prototipo estuvo sumergido unos 45 minutos y al sacarlo si ten铆a bastante humedad dentro, pero no ten铆a un "pozo de agua", la humedad si era suficiente para que en el tiempo da帽ara la electr贸nica. Se cree que las filtraciones fueron por las tapas de los sensores de presi贸n.xzx

Se dise帽a una nueva versi贸n de la carcasa, ahora sumando los requerimientos de priorizar materiales accesibles y disponibles en el mercado local. La geometr铆a inicial contempla un tubo de acr铆lico transparente, tapas y un soporte interno para la electr贸nica, adem谩s de espacios laterales para la salida de los sensores y cable UTP. Las tapas laterales realizan el sello total del dispositivo en esta versi贸n, mediante o'rings y fij谩ndose al soporte interno que es lo que mantendr谩 las tapas a presi贸n dentro del sistema generando la protecci贸n deseada IP69.


<p align="center"><img title="a title" alt="Alt text" src="images/Nodo completo.JPG" width="600px"></p>


Se realizan diferentes pruebas del nuevo prototipo, tanto a los componentes de sello de los sensores como al equipo completo en un ambiente controlado compuesto de un tubo de pvc de 6 metros de alto para simular la presi贸n de una columna de agua.

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_prototipo_1.jpg" width="300px"></p>

Finalmente, y luego de algunas iteraciones se logro un sistema sin filtraciones como observado en la foto de abajo :).

Se prueba este ptototipo luego en un pozo en el sector de Laguna Caren, aqu铆 se realizaron pruebas sumergiendolo a mayores profundidades progresivamente (10, 20, 30 y 40mt).

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_validacion_1.jpg" width="300px"></p>

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_validacion_2.jpg" width="300px"></p>

<!--
Hubo diferentes resultados, positivos donde carcasa permanecio sumergida sin filtraciones y otros donde ocurrieron filtraciones. Se observan algunos casos de carcasa con filtraciones m谩s abajo.
-->

Lo resultados fueron positivos y el sellado fue un 茅xito logrando una protecci贸n IP68. Hay leves filtraciones que se est谩n revisando luego de un tiempo prolongado dependiendo de como se tape la carcasa por lo que no se clasifica a煤n como ip69.

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_validacion_3.jpg" width="300px"></p>

### Cable de Comunicaci贸n

Adem谩s de la carcasa, se dise帽o el cable de comunicaci贸n entre el m贸dulo de captura de datos bajo el agua y el m贸dulo de comunicaci贸n en la superficie. Para ello se utiliza un cable UTP dentro de una manguera para evitar su corrosi贸n. El foco fue lograr un bajo costo lo que se logr贸 con 茅xito costando menos de la mitad que versiones comerciales. Este cable es el encargado de transportar los datos entre el m贸dulo de captura y el m贸dulo de comunicaci贸n.

<p align="center">
<img title="a title" alt="Alt text" src="images/carcasa_cable_manguera.png" height="250px">
<img title="a title" alt="Alt text" src="images/carcasa_cable_union.png" height="250px">
</p>

### Resultados

El equipo, o m贸dulo de captura de datos, una vez completamente armado tiene una forma cilindrica de un **tama帽o** de 55 cm de largo y 6,3 cm de radio.

<p align="center"><img title="a title" alt="Alt text" src="images/tama帽o_equipo_captura.png" width="600px"></p>

El **costo** de materiales se desprende de la carcasa y el cable de comunicaci贸n. El cable de comunicaci贸n puede variar su largo dependiendo de la aplicaci贸n, asumimos el mayor largo de 50 metros para la estimaci贸n.

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_costos.png" width="400px"></p>

Se alcanza un grado de **protecci贸n IP** IP66 pero de manera parcial, la carcasa no tiene un comportamiento confiable y est谩 pendiente iterar sobre el dise帽o.

> Tienes una consulta o comentario, escribenos a [openwater@niclabs.cl](openwater@niclabs.cl)


<!--
### Siguientes pasos
_\*(WIP mat铆as)\*_
_\*TODO: agregar informaci贸n sobre la manguera\*_
_\*TODO: agregar informaci贸n sobre tipo de ambiente para dise帽ar la carcasa (requerimiento)\*_
-->
<!--
Se puede ordenar el trabajo futuro en dos categor铆as dependiendo de su objetivo:

##### To Do's:

1. Disminuci贸n de costo de materiales.
2. Estandarizaci贸n de proceso de fabricaci贸n.

##### To Fix:

1. Revisar mecanismo de sellado y filtraciones.

-->

<!--

- mayores dificultades, tipos de pruebas, desaf铆os.

Dise帽o final y partes


## Instrucciones armado

Manual (Adjunto)

## Resultados pruebas

M茅todo de las pruebas

pruebas en tubo rancagua

pruebas en terreno

pruebas antes de llevar a terreno

Resumen de resultados y roadmap siguiente.

Comparaci贸n de costos cable vs cable nosotros.

- Tips
- Consejos
- Desaf铆os

Aprendizajes.

-->
