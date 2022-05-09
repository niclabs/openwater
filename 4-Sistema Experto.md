# Sistema Experto

El monitoreo continuo en el tiempo y análisis de caudales superficiales, niveles de agua subterránea y calidad química del recurso hídrico son esenciales para comprender el funcionamiento de un sistema hidrogeológico. Estos, a su vez, forman la base para que un/a experto/a en recursos hídricos, logre entender el funcionamiento natural de dicho sistema y distinguirlo de aquellos comportamientos anómalos. Algunos ejemplos de anomalías en los sistemas hidrogeológicos pueden ser los periodos de sequía, donde la disponibilidad, así como también la calidad del recurso hídrico, pueden verse afectados notablemente. Otro ejemplo también son los eventos de contaminación, donde la composición química del agua se ve afectada. De este modo, una rápida detección ante instancias anómalas es crítica para la planificación y toma de decisiones.

## A. Lógica de detección

La detección de instancias anómalas a través de variables medidas desde sistemas hidrogeológicos, como los acuíferos, se puede entender como una fusión de diversas herramientas de modelamiento, datos históricos, datos medidos (estado actual acuífero) y conocimientos de expertos con el fin de poder discriminar de manera eficiente la presencia de anomalías. Si este procedimiento de detección de anomalías se hace de manera automática, entonces podríamos definir esta “fusión” mediante el concepto de Sistema Experto, el cual es ampliamente usado en distintas áreas para apoyar a los operadores en la toma de decisiones. En el caso puntual de los acuíferos, el Sistema Experto puede ser de utilidad como apoyo en la toma de decisiones para la operación de estos acuíferos en cuanto a la ejecución de procedimientos preventivos o correctivos necesarios, dada alguna(s) anomalía(s) detectada(s).

<!-- El presente proyecto de investigación y desarrollo comprende dentro de su propuesta la elaboración de un Sistema Experto, el cual, mediante la información recopilada a partir de datos históricos, conocimiento experto humano, y mediciones actuales (desde nodos sensores) de temperatura, conductividad eléctrica y pH, turbiedad y nivel piezométrico sea capaz de detectar anomalías en acuíferos monitoreados. Un esquema que ejemplifica el concepto de Sistema Experto se muestra en la Figura 1. -->

<img title="a title" alt="Alt text" src="images\sistema_experto_diagrama_diseno.png">

El diseño considerado para el Sistema Experto consta del funcionamiento de dos herramientas (o modelos) de machine learning entrenadas para trabajar en paralelo, y cuyas salidas serán fusionadas a través de alguna estrategia determinada. Las herramientas de machine learning escogidas para esta propuesta son LightGBM y TabNet, las cuales, una vez que son entrenados, irán detectando anomalías en los acuíferos monitoreados, a medida que reciban mediciones en línea. Un ejemplo del flujo de información en el funcionamiento de esta metodología se muestra en la Figura 7.

<img title="a title" alt="Alt text" src="images\sistema_experto_diagrama_algoritmos.png">

Es importante mencionar que el Sistema Experto no se limita solamente a utilizar dos modelos (LightGBM y TabNet), su diseño hace que sea flexible para que puedan incorporarse otros tipos de modelos para trabajar en paralelo juntos a los ya propuestos.

En términos gráficos, la base de datos de validación, junto con las anomalías detectadas mediante la fusión de los modelos LightGBM y TabNet a través de la función lógica OR son visualizados en la Figura 15.

<img title="a title" alt="Alt text" src="images\sistema_experto_ejemplo.png">

De resultados obtenidos se desprende que ambos modelos por separado tienen un desempeño por sobre un 75% en prácticamente todas las métricas (solo el Recall para TabNet está por bajo un 75%, llegando a ser un 73%). Sin embargo, al fusionar ambos modelos, todas las métricas propuestas sobrepasan el 75% de desempeño requerido para alcanzar el hito, y considerando solo el Accuracy, éste logró alcanzar aproximadamente un 95%.

<!--
Tipos de Alarma
detección de anomalías
Ejemplos

Decir que esos tres elementos se encuentran para poder generar el tema.
Se busco poder juntar dos tipos de conocimientos, dato histórico más conocimiento humano. Que 
Anomalía. Comportamiento extraño de lo que se ha visto históricamente. De lo que se ve en el pasado una anomalía es un comportamiento no visto.


Diseño de s e se traduce en el acoplamiento de dos herramientas de ML, esta juntura con conocimiento humano se conforma en la detección de anomalías. Conjunga dos herramietnas de ML que al juntarse aumentan el diagrama de selección


Se tienen datos de P, T y Hum, en negro es el sistema experto y lo de abajo es lo que de verdad es anomalía.


Diseño
herramientas
y producto de sistema experto con datos que tenemos disponibles.



La interfaz es la visualización de todo un trasfondo que hay detras. Es la que toma todo el trabajo realizado por el ambiente de base de datos, es la conexión que permite a la per

-->


## B. Lógica de visualización

El Sistema Experto debe contemplar una capa de visualización, la cual ponga a disposición del usuario la información relacionada al acuífero que está siendo monitoreado. Esto implica la visualización de las variables medidas, así como también las anomalías detectadas por el sistema experto.

El sitio web es la culminación, y toma el trabajo realizado por todos los sistemas previos a él para presentar al usuario con la información y recomendaciones relevantes. Esto queda representado en la siguiente figura.

<img title="a title" alt="Alt text" src="images\sistema_experto_diagrama_visualización.png">

Para revisar el sitio web se puede entrar al  [enlace](http://agua.niclabs.cl:3001/) con las siguientes credenciales:



| Sitio web | [http://agua.niclabs.cl:3001/](http://agua.niclabs.cl:3001/#/) |
|-|-|
| user | pruebas |
| psas | fondefagua |

Se puede observar algunos flujos de trabajo del sitio en los siguientes Gif's. ¡Te invitamos a visitarla!.

<b>1. Visualización de datos de estación de monitoreo en el mapa.</b>

<img title="Gif sistema experto" alt="Alt text" src="images\sisexp_visualizacion_0datos.gif">

<b>2. Comparación de datos y análisis histórico en diferentes estaciones de monitoreo.</b>

<img title="Gif sistema experto" alt="Alt text" src="images\sisexp_visualizacion_1comparación.gif">

<b>3. Es posible descargar los datos de las estaciones de monitoreo en formato _.csv_.</b>

<img title="Gif sistema experto" alt="Alt text" src="images\sisexp_visualizacion_2descarga.gif">

<!--
|<img title="a title" alt="Alt text" src="images\sisexp_web_general.png">|
|-|
|Sitio web de visualización de datos|

|<img title="a title" alt="Alt text" src="images\sisexp_web_descarga.png" width = "500px">|
|-|
|Pestaña de descarga de datos|

|<img title="a title" alt="Alt text" src="images\sisexp_web_datos.png">|
|-|
|Visualización de datos recientes, es posible comparar entre estaciones|

|<img title="a title" alt="Alt text" src="images\sisexp_web_historico.png">|
|-|
|Visualización histórica de datos|
-->
