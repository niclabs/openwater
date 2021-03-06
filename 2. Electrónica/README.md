# 馃捇 Electr贸nica

## Dise帽o
El dispositivo de electr贸nica (nodo sensor) dise帽ado para el monitoreo de agua en intervalos de tiempo de manera aut贸noma, esta basado en tomar las medidas con sensores para ser enviadas mediante comunicaci贸n serial a un sistema de comunicaci贸n para el monitoreo de estas caracter铆sticas, este dispositivo tomar谩 medidas de pH, Conductividad, turbidez, temperatura y presi贸n.



### Prototipo
Como prototipo  se realiz贸 un circuito en Arduino para realizar pruebas con sensores, medidas y comunicaci贸n para obtener una versi贸n funcional que pudiera enviar los datos. Este prototipo su funcionamiento principal se basa en dos estados principalmente Reposo (Sleep), estado en el cual se esta en bajo consumo y sin trabajo de medidas y segundo activo que esta encargado de tomar las medidas de los sensores, guardar estos datos de manera codificada y enviarlos de manera serial con comunicaci贸n 485.

El funcionamiento b谩sico se puede ver en el siguiente diagrama:

<img title="a title" alt="Alt text" src="https://github.com/niclabs/openwater/blob/main/docs/images/Diagrama_func_simple.png">

#### Selecci贸n de componentes.
Dado lo anterior los componentes que integran este prototipo inicial son los siguientes:

1. **Arduino Nano:** Micro-controlador principal con el programa principal.
1. **ADC:** Lectura de se帽ales anal贸gicas a digitales de los sensores.
1. **RTC:** Encargado de establecer las alarmas de medida y env铆o al micro-controlar para llevar a cabos estas tareas.   
1. **Modulo SD:** Para el guardado de los datos medidos de manera codificada.
1. **Sensores:** Temperatura, conductividad, pH, Presi贸n y Turbidez. 
1. **RS485:** Para realizar una comunicaci贸n serial de gran alcance(>10m).

Destacar que estos sensores seleccionados se sometieron a una serie de pruebas para comprobar su rendimiento, ver sus limitaciones y desgaste en el tiempo explicado en mas destalle en el apartado de sensores.

Por otra parte la conexi贸n entre estos componentes esta dado se manera simplificada en el diagrama a continuaci贸n:

<img title="a title" alt="Alt text" src="https://github.com/niclabs/openwater/blob/main/docs/images/Diagrama_bloque_simple.png">
<img title="a title" alt="Alt text" src="https://github.com/niclabs/openwater/blob/main/docs/images/electronica_conexiones_prototipo.png" width="400px">

Donde los sensores TDS, pH y turbidez poseen su electr贸nica, el de presi贸n entrega sus valores al ADC y el de temperatura mediante comunicaci贸n "OneWire" directamente al micro-controlador. El m贸dulo SD se comunica con el micro-controlador a trav茅s de conexi贸n "ISCP", en cambio el ADC posee una conexi贸n I2C para tener las se帽ales de los 4 sensores y por 煤ltimo la informaci贸n de los sensores es enviada de manera serial al componente 485 y es enviada mediante los canales A y B. 

Como resultados iniciales se tiene un nodo sensor capaz de obtener medidas, guardar estos datos en una microSD y adem谩s enviar estos datos de manera serial siendo un prototipo inicial lo suficientemente 煤til para la realizaci贸n de pruebas en profundidad y analizar las limitaciones de los sensores bajo condiciones en profundidad controlada.

<img title="a title" alt="Alt text" src="https://github.com/niclabs/openwater/blob/main/docs/images/electronica_prototipo_armado.png" width="500px">

### PCB
Continuando con las mejoras del nodo sensor, y el prototipo funcionando de manera adecuada, si bien es un dispositivo apto para la realizaci贸n de pruebas controladas, se busca un dispositivo m谩s apto en terrenos reales, como profundidades de aguas de al menos 30 metros. Para ello se realiz贸 una integraci贸n den PCB con un fabricante local de PCB y dise帽o de circuitos, pasando prototipo a una PCB con mejoras incluidas dadas principalmente en el sistema de energ铆a y espacio:

1. **Fuente energ茅tica con bater铆as:** Agregar al nodo un circuito de energ铆a que sea alimentado a trav茅s de bater铆as de litio 18650 con toda su electr贸nica para un correcto funcionamiento (Cargadores y elevadores).
2. **Distribuci贸n energ茅tica de componentes:** Dividir la fuente de energ铆a en una activa (5V) que siempre entrega alimentaci贸n al sistema y una de reposo (5Vs) que se apaga cuando el sistema no esta midiendo o enviado datos para aquellos componentes que puedan ser apagados para reducir el consumo lo mayor posible.
3. **Reducci贸n de espacio para Carcasa:** Optimizar el espacio creando un dispositivo con la electr贸nica m谩s compacto para la utilizaci贸n de la carcasa especial que fue dise帽ada especialmente para ser m谩s apta al sumergirse.

<img title="a title" alt="Alt text" src="https://github.com/niclabs/openwater/blob/main/docs/images/diagrama_alimentacion.png">

La PCB incluye toda la electr贸nica de sensores y las necesarias  como reguladores de voltaje (-5V,3V,-3V y 3.3V) para componentes y electr贸nica siendo una pieza completa que se insertan los sensores para tomar las medidas. Posee adem谩s una conexi贸n FTDI para realizar la programaci贸n del micro-controlador y un interruptor para utilizar comunicaci贸n serial directa al micro-controlador en vez de la 485 para la realizaci贸n de pruebas.

<img title="a title" alt="Alt text" src="https://github.com/niclabs/openwater/blob/main/docs/images/PCBnombrada_v0.png">



#### Historial de Versiones

Debido a diversos tipo de situaciones como falta de pistas o distribuciones de los componentes en diferentes fuentes de energ铆a (5V y 5Vs) o simple optimizaci贸n de esta, se obtuvieron diferentes versiones de PCB como modificaciones diferenciadas principalmente en la distribuci贸n energ茅tica a modo mejora,  estas versiones y modificaciones est谩n resumidas en la siguiente tabla.

|       PCB         |                  **Modificaci贸n**                 |                    **Caracter铆sticas**                   |                         **Resultado**                        |                              **Problemas**                             |
|----------------|:--------------------------------------------|:--------------------------------------------------------|:------------------------------------------------------------|:----------------------------------------------------------------------|
|    **Versi贸n 1.a**    | Primera PCB fabricada                        | Distribuci贸n de alimentaci贸n en reposo y continua.       | Placa completamente funcional                                | La alimentaci贸n de reposo solo esta conectada con el componente RS485. |
| Versi贸n 1.b | Corte y cambio de pistas para la PCB inicial | Distribuci贸n energ茅tica de componentes mas eficiente.    | Reducci贸n del consumo en estado activo.                      | Componente RS485 de alto consumo en reposo                               |
| Versi贸n 1.c | Cambio de componente RS485 manualmente        | Optimizaci贸n de consumo en reposo                         | Problema funcional de la placa, (mala practica de soldadura) | PCB sin funcionamiento. |
|    **Versi贸n 2.a**    | PCB con enrutado nuevo                      | Componentes divididos en su mayor铆a correctamente         | Placa completamente funcional                                | RS485 de alto consumo y en alimentaci贸n continua, falta de una pista.  |
|    **Versi贸n 3.a**    | PCB con enrutado nuevo                      | Correcci贸n de la pista faltante de la versi贸n anterior. | Placa completamente funcional                                | RS485 de alto consumo y en alimentaci贸n continua.                      |

Estas versiones se ejemplifican en esquemas a continuaci贸n para detallar los cambios de distribuci贸n energ茅tica de los componentes que son alimentados con 5Vs y 5v respectivamente.

<img title="a title" alt="Alt text" src="https://github.com/niclabs/openwater/blob/main/docs/images/diagrama_versiones.png">


## Fabricaci贸n

Con los archivos de una versi贸n funcional del sistema (Versi贸n N掳2), se realiz贸 un estudio en la fabricaci贸n de esta placa para tener una idea y obtener un an谩lisis en t茅rminos de los costos que tiene finalmente el "nodo sensor". 


### Cotizaci贸n:
Para cotizar se consider贸 la posibilidad de una fabricaci贸n y ensamblaje completamente externo con los componentes entregados por el fabricante.

#### 1. Fabricaci贸n y ensamblaje externo:
Consideraciones:
 * Para esta cotizaci贸n se tomaron en cuenta los fabricantes: JLCPCB, PCBway, PCBgogo, EEcart, SeedStudio.
 * Los precios obtenidos son dados en base a cotizaciones r谩pidas entregadas por los fabricantes.
 * Los archivos requeridos para las cotizaciones Gerber (PCB), BOM (componentes) con un formato espec铆fico para cada fabricante y el *"pick and place"* en algunos casos.
 * La cotizaci贸n fue realizada para una cantidad de 5 PCBs ensambladas (cantidad m铆nima aceptada).

 #### 2. Fabricaci贸n externa y ensamblado local:
 La cotizaci贸n de esta opci贸n la placa es fabricada de manera externa y los componentes cotizados a los distribuidores.

 Consideraciones:
* El ensamblaje se consider贸 de manera manual.
* Utilizaci贸n de stencil para el ensamblado.
* Se realiz贸 una cotizaci贸n de 5 placas.
* No todos los componentes son f谩ciles de obtener, se tiene que buscar sustitutos dependiendo del stock.
* Digikey y Mouser como distribuidores de componentes (al ser los mas completos).
#### 3. Comparaci贸n de opciones:

Dado el detalle del valor de componentes se hace una comparaci贸n entre las 2 opciones de fabricado,se consider贸 EEcart y PCB como fabricantes por ser las mejores opciones. adem谩s de una fabricaci贸n completa externa con una optimizaci贸n de precios en componentes (RTC,pH), por un lado el RTC tiene un precio elevado y por otro el conector de pH se adquiere con el sensor.

Resultados y precios:

|                             | **Total (5u)** | **Total+ 30%** | **Precio unitario** | **Tiempo**  |
|-----------------------------|----------------|----------------|---------------------|-------------|
| **Local**                   | $772.09        | $1003.72       | $200.74             | 3-4 semanas |
| **Externa EEcart**          | $907.26        | $1179.44       | $235.89             | 5 semanas   |
| **Externa PCBWay**          | $888.45        | $1176.19       | $231.00             | 5.5 semanas |
| **Externa PCBWay (RTC,pH)** | $705.06        | $916.58        | $183.32             | 5 semanas   |


Considerar adem谩s un precio extra en cuando a sensores y bater铆as del dispositivo de $100.92USD/unidad aprox.

#### 4. Pros y contras

|    Fabricaci贸n Local    | Fabricaci贸n Externa |
|-----------------------------|----------------|
| - Menos tiempo estimado de realizaci贸n. <br> - Menor precio estimado. <br> - Ensamblado manual. <br> - Dificultad de obtenci贸n de algunos componentes (stock limitado).  |      - La placa llega para usar directamente. <br> - Margen de optimizaci贸n. <br> - Mayor tiempo de espera. <br> - Mayor precio.       |

### Programaci贸n
Hablando del software del dispositivo nodo sensor se poseen 2 versiones  con y sin SD para su funcionamiento, estos posee las siguientes caracter铆sticas:
1. **Posee variables de los per铆odos de medida y env铆o de datos**: Es una de las caracter铆sticas m谩s importantes para la definici贸n de tiempos de funcionamiento del sistema. La variable "Freq_sens" indica cada cuantos segundos tomada una medida de los sensores y la variable "Freq_send" representa el intervalo en segundos en el que son enviados los datos, claramente  Freq_send > Freq_sens  ya que deben existir datos medidos para ser enviados.
2. **Codificaci贸n de lectura de datos**: Para realizar un env铆o m谩s eficiente ya sea por velocidad, memoria, disminuci贸n de consumo energ茅tico en el momento de enviar datos se desarroll贸 una librer铆a que codifique los datos para ello. Lo importante a destacar es que existe una codificaci贸n de lectura y otra de env铆o explicada mas adelante.

La codificaci贸n de lectura simplemente pasa a bytes(9) la medida (valor) del sensor, tiempo(timestamp) dado por la alarma de medida del RTC en formato "Unix" y su ID del sensor (valor predeterminado).

3. **Guardado de datos en un "DataBlock"**: Los datos de cada intervalo, es decir, el tipo (sensor ID), su valor y tiempo de medida (Timestamp) en cada sensor son codificados (explicado m谩s adelante) en bytes al que llamaremos "sensor reading", estos son generados en cada medida y ser谩 guardado en el "Datablock" (arreglo) de 512 bytes que actuara como memoria RAM-buffer. Los "sensor reading" son lo que poseen la codificaci贸n de lectura con un largo de 9 bytes para el guardado de los datos. Dado esto la estructura del Datablock esta dada por 2 bytes para llevar el conteo de medidas, 504 bytes para "sensor reading" (56 medidas u 11 medidas de 5 sensores) y 6 bytes sobrantes como se puede ver a continuaci贸n.

Para el caso de la sd cuando el DataBlock esta lleno guarda los datos en archivos binarios dentro de la tarjeta SD y los env铆a junto a los valores del arreglo cuando sea el tiempo de enviado con una codificaci贸n nueva para el enviado. Si es la versi贸n sin sd no se posee m谩s memoria que la del arreglo por lo que esta limitado a medir una cantidad m谩xima de datos antes de enviar, por lo que la "Freq_send" tiene esta limitante, por ejemplo,un m谩ximo de 11 veces la Freq_sens para 5 sensores para no perder datos en la codificaci贸n base.

<img title="a title" alt="Alt text" src="https://github.com/niclabs/openwater/blob/main/docs/images/datablock.png">

4. **Codificaci贸n par env铆o de datos** : Para reducir la cantidad de tama帽o de los datos enviados y as铆 realizar un env铆o m谩s r谩pido con menor consumo, se realizaron distintos tipos de codificaci贸n de enviado a modo de reducir el tama帽o de los datos.
* Codificaci贸n de env铆o base:  Para esta codificaci贸n y las siguientes se define un nuevo bloque "Sensing Unit", que se divide en 1byte "Header" que posee la informaci贸n del tipo de codificaci贸n y la ID del sensor y 6 bytes "Payload" que contiene 4bytes para el Tiemstamp y solo 2bytes para el valor del sensor, esta reducci贸n ene le valor del sensor se debe a que los valores de los sensores al ser peque帽os pueden ser perfectamente representados en 2bytes. Reduciendo la unidad "sensor reading" de 9bytes a la unidad "Sensing Unit Base" de 7bytes.
* Las dem谩s codificaciones se pueden encontrar en detalle en la documentaci贸n.

<img title="a title" alt="Alt text" src="https://github.com/niclabs/openwater/blob/main/docs/images/sensing_unit_base.png">



5. **Los datos son enviados como paquetes de bytes**: Como los datos son codificados a bytes estos son enviados de esta manera en paquetes de bytes a trav茅s de comunicaci贸n serial RS485 estos est谩n dados por un tama帽o m谩ximo de 51 bytes, es decir, 7 Sensing Unit (49 bytes) y 2 bytes para detecci贸n de errores. Este tama帽o se define debido a que es el tama帽o m铆nimo de un paquete en LoRa (m贸dulo de comunicaci贸n inal谩mbrica utilizada en la superficie del sistema).



## Roadmap

Finalizado el nodo sensor actual si bien es funcional aun est谩 en estapa de mejora para lograr un dispositivo lo m谩s completo posible, dentro de las cuales relacionadas directamente en el 谩rea energ茅tica, costos y espacio principalmente, resumidos en la siguiente tabla con mejoras que se est谩n realizando.

| **Cambio**    | **Descripci贸n**                                                                                                                                                                                                                                     |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Energ茅tico** | Para lograr mas autonom铆a se est谩n desarrollando cambios para reducir el consumo energ茅tico,   ya sea alternativas de componentes de menor consumo, otras fuentes energ茅ticas, remover algunos componentes o directamente en el programa principal. |
| **Costo**      | Una de las principales caracter铆sticas a reducir, con lo que se considera remover componentes,  creaci贸n de una versi贸n Lite de menor costo con menores funcionalidades,                                                                            |
| **Espacio**    | Reducir el espacio no es lo esencial pero trae beneficios de ser m谩s pr谩ctico, de cual se ve la  reducci贸n de componentes como cargadores, cambios de componentes a menor tama帽o y redistribuci贸n de los componentes en la PCB.                     |