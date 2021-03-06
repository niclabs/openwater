# 馃捇 Electr贸nica

### Dise帽o

La electr贸nica se encarga de obtener las se帽ales el茅ctricas o datos de los sensores, almacenarlos, comunicarlos y realizar todas las tareas y mecanismos necesarios para garantizar que la toma  y comunicaci贸n de datos funcione en los momentos, tiempos y cantidad esperados.

En este trabajo los sensores se utilizan en experimentos de calidad, pruebas de comunicaci贸n y en prototipado, entre otros, por lo que se dise帽aron diferentes electr贸nicas para los diferentes usos internos. Pero por lo general ten铆an en com煤n un esquema como el siguiente que cuenta con un reloj, una memoria y conexi贸n de los diferentes sensores a un procesamiento:

<p align="center"><img title="a title" alt="Alt text" src="images/electronica_conexiones_prototipo.png" width="400px"></p>

Abajo se observa una implementaci贸n de este equema para pruebas de los sensores. El prototipo guarda los datos en una microSD y los comunica por puerto serial para verlos en tiempo real.

<p align="center"><img title="a title" alt="Alt text" src="images/electronica_prototipo_armado.png" width="500px"></p>

### Prototipado

Para le electr贸nica a sumergir bajo el agua se trabaj贸 en la integraci贸n de todos los componentes en una PCB. Esta nueva placa debe tener el tama帽o y funcionalidades suficientes para ser sumergida junto a la carcasa dise帽ada en la secci贸n [Carcasa](es/Carcasa.md).

Para otorgarle autonom铆a se suman dos nuevas funcionalidades:
1. **Fuente energ茅tica a bater铆as:** Agregar bater铆as de litio 18650 con electr贸nica correspondiente para un correcto funcionamiento (cargadores y elevadores).
2. **Distribuci贸n energ茅tica de componentes:** Dividir la fuente de energ铆a en una que apaga los sensores cuando no est谩n midiendo para reducir el consumo.

<p align="center"><img title="a title" alt="Alt text" src="images/electronica_pcb_componentes.jpg"></p>

Se reviso factibilidad y detalles del proceso para fabricaci贸n de la placa, se vieron dos opciones principales:

1. Opci贸n Externa: Fabricar y ensamblar en el extranjero
2. Opci贸n Local: Fabricar placa en el extranjero y ensamblar componentes localmente.

<!-- La segunda opci贸n implica hacer el trabajo de comprar todos los componentes de la placa y soldarlos. Sus ventajas son la posible reutilizaci贸n de componentes dificiles de encontrar desde la electr贸nica original de los sensores y una consecuente optimizaci贸n de costos. -->

Ambas opciones tiene un costo cercano a los 200 dolares americanos por placa. Puede ser importante evaluar la disponibilidad de componentes para decidir por una opci贸n.

**Importante:** Considerar adem谩s un precio extra en cuando a sensores y bater铆as del dispositivo de $100.92USD/unidad aprox.

<!--
|   Cotizaciones  | **Total (5u)** | **Total+ 30%*** | **Precio unitario USD** | **Tiempo**  |
|-----------------------------|----------------|----------------|---------------------|-------------|
| **Opci贸n Local**                   | $772.09        | $1003.72       | $200.74             | 3-4 semanas |
| **Opci贸n Externa EEcart**          | $907.26        | $1179.44       | $235.89             | 5 semanas   |
| **Opci贸n Externa PCBWay**          | $888.45        | $1176.19       | $231.00             | 5.5 semanas |
-->

### Uso y programaci贸n

<p align="center"><img title="a title" alt="Alt text" src="images/PCBnombrada_v0.png"></p>

##### Materiales

1. Componentes externos
    a.  Bater铆as 18650
    b.  Tarjeta SD
    c.  Pila Reloj
2. Para programar
    a. Cable de energ铆a
    b. Cable de programaci贸n (FTDI)
3. Sensores

##### Programaci贸n

1. PCB debe estar alimentada por bater铆a o cable de energ铆a.
2. Conectar un **adaptador FTDI-USB** en el puerto FTDI de la PCB por un lado y en puerto USB del computador por el otro.
3. Dejar el **interruptor en FTDI** (se encuentra al lado de conexi贸n a programador).

    <br>
    (La programaci贸n se realiza en Arduino IDE y el programa se encuentra en el siguiente [enlace](https://github.com/niclabs/water-monitoring/tree/master/6.%20Electr%C3%B3nica/PCB-MCI/Codigo_Final).
    <br>
    <br>

4. Seleccionar **el puerto** de conexi贸n correspondiente en la pesta帽a herramientas.
5. Seleccionar  **Arduino Uno** en la pesta帽a herramientas.

<p align="center"><img title="a title" alt="Alt text" src="images/electronica_pcb_programacion_arduino.png" width="400px"></p>

6. Presionar "Subir c贸digo".

### Resultados

La placa tiene un **tama帽o** de  22,5 cm largo x 3,2 cm ancho x 1,7 cm de alto con todas sus piezas soldadas y presenta una **autonom铆a** de 27 d铆as con dos bater铆as que suman un total de 5000 mAh. 

El **costo** de fabricar una placa PCBN ronda los USD\$200 m谩s USD\$100 aproximadamente para componentes externo para el funcionamiento de la placa.

<br>

> Tienes una consulta o comentario, escribenos a [openwater@niclabs.cl](openwater@niclabs.cl)


<!-- ## Archivos Importante
**Para mayor detalle sobre el dise帽o, archivos fuente, costos, etc, puede encontrarlos en el repositorio:**
[Electr贸nica](https://github.com/niclabs/openwater/tree/main/2.%20Electr%C3%B3nica)
-->


<!--
### Siguientes pasos

#### To Do's
_\*(Secci贸n WIP mat铆as)\*_

1. Disminuir costo de fabricaci贸n.
2. Mejorar autonom铆a del sistema.
-->
