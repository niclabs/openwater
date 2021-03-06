
# 馃摗 Comunicaci贸n Inal谩mbrica

## Introducci贸n
Se muestra el diagrama completo de conectividad de la soluci贸n. El sistema de comunicaci贸n a implementar utiliza un medio guiado para la comunicaci贸n entre el m贸dulo de captura, ubicado en el fondo de la masa de agua y el m贸dulo de comunicaci贸n, ubicado en la superficie. Se utiliza la tecnolog铆a LoRaWAN para la transmisi贸n de datos entre el m贸dulo de comunicaci贸n y el network server. Finalmente la comunicaci贸n entre el Network Server y el Sistema Experto es a trav茅s de tecnolog铆a Web utilizando el protocolo HTTP. Los datos de los sensores son almacenados en una Base de Datos para ser posteriormente procesados por el sistema experto.

<p align="center" style="font-style: italic;color:#8F9A9B"><img title="a title" alt="Alt text" src="images/diagrama_bloques_solucion.PNG" width="550px"> Diagrama de bloques de la soluci贸n </p>

## Nodo Sensor
### M贸dulo de Captura
El m贸dulo de captura est谩 compuesto por cuatro elementos:

 * Sensores o transductores: referirse a la secci贸n [Sensores](0-Sensores.md). 
 * Placa Electr贸nica o PCB: referirse a secci贸n [Electr贸nica](1-Electr贸nica.md).
 * Cable de par trenzado: referirse a secci贸n [Sesnores/Cable de comunicaci贸n](2-Carcasa.md?id=cable-de-comunicacion)
 * Carcasa sumergible: referirse a secci贸n [Carcasa](2-Carcasa.md)


El env铆o de datos desde el m贸dulo de captura al m贸dulo de comunicaci贸n es a trav茅s del protocolo serie RS485. Para ello ambos m贸dulos cuentan con un conversor de protocolo de comunicaci贸n UART a RS485 como se muestra abajo. El medio f铆sico que une ambos m贸dulos es un cable de par trenzado del tipo UTP (unshielded twisted pair) dentro de una mangera para poder sumergirlo.

<p align="center"><img title="a title" alt="Alt text" src="images/comunicacion_serial.PNG"></p>

Figura 3. Diagrama de bloques para la comunicaci贸n entre m贸dulos en el nodo sensor


### M贸dulo de Comunicaci贸n

El m贸dulo de comunicaci贸n est谩 compuesto por 2 elementos:

 * subm贸dulo LoPy4: encargado del procesamiento de la informaci贸n serial proveniente del m贸dulo de captura. Adem谩s tiene la responsabilidad de enviar las medidas a trav茅s del canal inal谩mbrico utilizando tecnolog铆a LoRaWAN.
 * subm贸dulo RS-485: encargado de convertir la comunicaci贸n serial RS-485 proveniente del m贸dulo de captura a est谩ndar UART para que pueda ser procesada por el subm贸dulo LoPy4.

Para poder realizar la implementaci贸n se considera el diagrama de una red LPWA (Low Power Wide Area) definida en *[1]*, el cual considera cuatro bloques: End-Nodes, Concentrado/Gateway, Network Server y Application Server tal como lo muestra la figura 6. El m贸dulo de comunicaci贸n del nodo sensor representa a un End-Node en la arquitectura LPWA.

<p align="center"><img title="a title" alt="Alt text" src="images/lorawan.PNG"></p>

Figura 6. Arquitectura LoRaWAN. Tomada de [1].

El nodo LoPy4 es una placa de desarrollo que soporta cuatro tipos de red (LoRa, Sigfox, WiFi, Bluetooth). Adem谩s implementa MicroPython, una versi贸n eficiente del lenguaje de programaci贸n Python 3 que incluye un peque帽o subconjunto de la biblioteca est谩ndar de Python y est谩 optimizado para ejecutarse en microcontroladores y en entornos restringidos, como el microcontrolador ESP32. La figura 7 muestra el m贸dulo de comunicaci贸n antes de ser ensamblado. La figura 8 muestra el m贸dulo de comunicaci贸n ensamblado.



<p align="center"><img title="a title" alt="Alt text" src="images/nodo_comunicaciones.PNG"></p>

Figura 7. M贸dulo de Comunicaciones con todas sus partes (antes de ser ensamblado)

<p align="center"><img title="a title" alt="Alt text" src="images/nodo_comunicaciones_2.PNG"></p>

Figura 8. M贸dulo de Comunicaciones con todas sus partes (despu茅s de ser ensamblado)

## Red LPWA


Como se indic贸 en la secci贸n anterior, el m贸dulo de comunicaci贸n del nodo sensor, cumple el rol de End-node en una red LoRaWAN (ver figura 6). Los otros componentes de la red son implementados de la siguiente manera:

 * El Concentrador o Gateway: este elemento es desplegado utilizando un Radio Gateway marca RAK modelo 7240.
 * El Network Server: es implementado a trav茅s del proyecto opensource The Things Network (https://www.thethingsnetwork.org/). Este proyecto permite crear aplicaciones que reciben los mensajes LoRaWAN provenientes desde los End-Nodes y los reenvia hacia un Application Server, que en nuestro caso es el Sistema Experto.

## Sistema Experto

El sistema experto representa al Application Server de una arquitectura LoRaWAN (ver figura 6). Luego que los mensajes LoRaWAN son recibidos por el Network Server, son enviados al Sistema Experto a trav茅s de mensajes HTTP. El flujo de mensajes se describe en la figura 9.

<p align="center"><img title="a title" alt="Alt text" src="images/paquetes.PNG"></p>

Figura 9. Flujo de mensajes entre el m贸dulo de captura y el Sistema Experto

El sistema experto procesa los mensajes HTTP y extrae las medidas provenientes de un nodo sensor. Luego, por cada medida obtenida, se almacena en la base de datos los siguientes datos:

 * ID del nodo sensor
 * ID del transductor
 * Marca de tiempo en la que se realiz贸 la medida
 * Valor de la medida

<!--
## Resultados

- Distancia
- RSSI, SNR
- Autonom铆a
- Tasa de error en el cable de comunicaci贸n.
-->

----

[1] http://thethingsnetwork.org/docs/lorawan/architecture.html


<br>

> Tienes una consulta o comentario, escribenos a [openwater@niclabs.cl](openwater@niclabs.cl)

