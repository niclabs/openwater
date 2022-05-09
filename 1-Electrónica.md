# 💻 Electrónica

### Diseño

Primeras versiones del sistema de captura de datos tenían el objetivo de ser utilizados para realizar los experimentos con los sensores y prototipar primeras versiones de la electrónica que se sumergiría en el agua.

Las funcionalidad de ambos es casi la misma: leer sensores ambientales, almacenar datos temporales. Para el caso del prototipo a sumergir en los acuíferos la información además debe ser comunicada al exterior y debe poder funcionar de manera autónoma por semanas a las vez.

<img title="a title" alt="Alt text" src="images/electronica_conexiones_prototipo.png" width="400px">

Como resultados iniciales se tiene un nodo sensor capaz de obtener medidas, guardar estos datos en una microSD y además enviar estos datos de manera serial siendo un prototipo inicial lo suficientemente útil para la realización de pruebas en profundidad y analizar las limitaciones de los sensores bajo condiciones en profundidad controlada.

<img title="a title" alt="Alt text" src="images/electronica_prototipo_armado.png" width="500px">

### Prototipado

Junto a la electrónica anterior, se trabajó en la integración de todos los componentes en una PCB. Esta nueva placa debe tener el tamaño y funcionalidades suficientes para ser sumergida junto a la carcasa diseñada (más información en XXXX).

Se agregan dos nuevas funcionalidades:
1. **Fuente energética con baterías:** Agregar al nodo baterías de litio 18650 con toda su electrónica para un correcto funcionamiento (cargadores y elevadores).
2. **Distribución energética de componentes:** Dividir la fuente de energía en una que apaga los sensores cuando no están midiendo para reducir el consumo.

<img title="a title" alt="Alt text" src="images/electronica_pcb_componentes.jpg">

Se reviso factibilidad y detalles del proceso para fabricación de la placa, se vieron dos opciones principales:

1. Opción Externa: Fabricar y ensamblar en el extranjero
2. Opción Local: Fabricar placa en el extranjero y ensamblar componentes localmente.

<!-- La segunda opción implica hacer el trabajo de comprar todos los componentes de la placa y soldarlos. Sus ventajas son la posible reutilización de componentes dificiles de encontrar desde la electrónica original de los sensores y una consecuente optimización de costos. -->

Ambas opciones tiene un costo cercano a los 200 dolares americanos por placa. Puede ser importante evaluar la disponibilidad de componentes para decidir por una opción.

**Importante:** Considerar además un precio extra en cuando a sensores y baterías del dispositivo de $100.92USD/unidad aprox.

<!--
|   Cotizaciones  | **Total (5u)** | **Total+ 30%*** | **Precio unitario USD** | **Tiempo**  |
|-----------------------------|----------------|----------------|---------------------|-------------|
| **Opción Local**                   | $772.09        | $1003.72       | $200.74             | 3-4 semanas |
| **Opción Externa EEcart**          | $907.26        | $1179.44       | $235.89             | 5 semanas   |
| **Opción Externa PCBWay**          | $888.45        | $1176.19       | $231.00             | 5.5 semanas |
-->

### Uso y programación

<img title="a title" alt="Alt text" src="images/PCBnombrada_v0.png">


Para utilizar la placa considerar los siguientes materiales:

- Componentes externos
    - Baterías 18650
    - Tarjeta SD
    - Pila Reloj
- Para programar
    - Cable de energía
    - Cable de programación (FTDI)
- Sensores

Para programar la placa considerar los sigueintes pasos generales:

1. PCB debe estar alimentada por batería o cable de energía.
2. Conectar un **adaptador FTDI-USB** en el puerto FTDI de la PCB por un lado y en puerto USB del computador por el otro.
3. Dejar el **interruptor en FTDI** (se encuentra al lado de conexión a programador).

La programación se realiza en Arduino IDE y el programa se encuentra en el siguiente [enlace](https://github.com/niclabs/water-monitoring/tree/master/6.%20Electr%C3%B3nica/PCB-MCI/Codigo_Final). Para cargar el programa continuar con los pasos:

4. Seleccionar **el puerto** de conexión correspondiente en la pestaña herramientas.
5. Seleccionar  **Arduino Uno** en la pestaña herramientas.
<img title="a title" alt="Alt text" src="images/electronica_pcb_programacion_arduino.png" width="400px">
6. Presionar "Subir código".

### Siguientes pasos

#### To Do's
_\*(Sección WIP matías)\*_

1. Disminuir costo de fabricación.
2. Mejorar autonomía del sistema.
