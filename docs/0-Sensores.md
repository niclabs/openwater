# Sensores

<!--
TODO: poner modelo de sensores de referencia.
TODO: poner cosas que salieron mal: medicion presión a 40cm, ...)
TODO: poner fotos de todos los experimentos para todos.
TODO: terminar de analizar íultimos datos.
TODO: poner tabla de resuemn resultados sensores.
-->

<!--
- poner figura de calidad de la medición vs costo
    - buscar tmbn alguna explicación en los informes
- poner figura del sistema completo donde sensores es input
-->

<img title="a title" alt="Alt text" src="images/sensor_agua.png">

La calidad de los datos generados que alimenten el sistema afecta directamente su desempeño y la calidad de información presentada a los usuarios del sistema, por esto los sensores a utilizar son de vital importancia. Pero a la vez mejores sensores implican un mayor precio, y el objetivo del proyecto es generar un sistema de bajo costo.

Dada esta carcterística, la caracterización del comportamiento de los sensores y definición de sus alcances permite generar un óptimo equilibrio entre costo de los equipos y desempeños esperados del sistema para los casos relevantes de uso, en los rangos definidos.

El objetivo es encontrar dispositivos de un costo bajo pero cuya calidad de medición sea la suficiente para operar el sistema. Muchas veces sensores industriales o profesionales pueden estar sobrestimados para la aplicación específica y tener una presición mayor de la necesaria para un análisis de las dinámicas y anomalías de acuíferos.

En la siguiente table encontramos los sensores en proceso de pruebas para medir 5 variables fisicoquímicas relevantes:

| Variable | Modelo Sensor | Rango | Error | Resolución |
| -------------------------- | -------------------------------- | ------------------------------------------- | ---------------------------------- | -------------------------------- |
| Tº | - [DS18B20](https://altronics.cl/sensor-sonda-temperatura-ds18b20?search=ds18b20)  | \-10°C - 85°C | ±0.5 ºC | 0,0625 °C<br>(12 bit) |
| Presión  | - [HK1100C](https://altronics.cl/sensor-presion-hk1100c) <br> - [Gravity Pressure](https://www.dfrobot.com/product-1675.html)| 0 - 1,2 MPa | 1.5% | 18 kPa<br>1.8 mt H2O |
| pH | - [Gravity: Analog pH Sensor/Meter](https://www.dfrobot.com/product-1025.html)  | 0 - 14 pH | ±0,1 pH | 0,014 pH<br>(12 bit) |
| Conductividad Eléctrica | - [Gravity: Analog TDS Sensor/Meter](https://www.dfrobot.com/product-1662.html) <br> -[]()| 0 - 1000ppm<br>0 - 2000 uS/cm<br>0 - 2mS/cm | ± 10% FS<br>200 uS/cm<br>0.2 mS/cm | 1,3 ppm<br>2,6 uS/cm<br>(12 bit) |
| Turbiedad | - [Grove - Turbidity Sensor/Meter](https://www.dfrobot.com/product-1394.html) <br> - [Sensor turbidez](https://altronics.cl/sensor-turbidez-liquidos) | 0 - 3000 NTU | No indica | 4,5 NTU<br>(12 bit) |

Se sometió a los sensores a tipos de pruebas que permitieran evaluar dos dimensiones principales de su comportamiento: (1) su presición y (2) su desempeño por periodos prolongados de sumersión en medio acuático ('sensor drift').

Para esto se utilizó baldes de agua en condicinoes controladas que simulan las condiciones en un acuífero y un sistema de captura de datos para luego procesarlos.

<img title="a title" alt="Alt text" src="images/sensor_temp_experimento1.png" width="300px">

El resumen de los experimentos actuales puede verse en la siguiente tabla:

| Variable                   | Estado | Comentario |
| -------------------------- | ------ | ----------- |
| Temperatura | ✅ Aprobado para proseguir experimentos | Operación dentro de lo esperado. Error menor a 0.5 ºC y buen desempeño en sumersión continua |
| Presión     | ✅ Aprobado para proseguir experimentos | Operación dentro de lo esperado. Error menor a 1cm y buen desempeño en sumersión continua |
| pH          | ✅ Aprobado para proseguir experimentos | Operación dentro de lo esperado. Error menor a 1 y buen desempeño en sumersión continua |
| Conductividad Eléctrica | ⚠️ En evaluación | Buena calidad de medición pero presentó problemas en sumersión continua. Se realizarán nuevos experimentos |
| Turbiedad   | ❌ Reprobado | Error muy alto (mayor a 1000 TPU) y sensor muy sensible a variables externas |

#### Notas

Algunos comentarios sobre los diferentes sensores:
##### - Temperatura:

<img title="a title" alt="Alt text" src="images/sensor_temp.png" width="200px">

Experimentos demostraron un buen desempeño del sensor en su comportamiento en el tiempo. Algunas observaciones:

- Comportamiento muy predecible, después de un tiempo se puede observar una muy leve desviación lineal constante de la medidas, pero se puede corregir completamente reajustando un offset.
- Errores menores a 0.5ºC luego de 2 meses  de uso prolongado sin recalibrar. Luego de 9 meses de uso error en mediciones aumento pero se mantiene menor a los 0.5ºC al recalibrar. 

<img title="a title" alt="Alt text" src="images/sensor_temp_plot_hist.png">

##### - Conductividad:

<img title="a title" alt="Alt text" src="images/sensor_tds.png" width="300px">

Algunas observaciones:

- Al medir dos al mismo tiempo se afectan la medida.
- Es súper clara la medición dentro del rango de 0 - 1500 uS/cm.
    - Al medir hasta 1500 uS/cm errores se mantienen bajo los 50 uS/cm. Al medir hasta 2000 uS/cm error medio se mantiene entre 100 - 200 uS/cm.

- Luego de 3 meses de uso continuo, sensor pierde su calibración Se esperan más experimentos para ver si es por depositos de minerales en el sensor, o si es corregible, o fue un error puntual, o etc.
- No se ve histéresis importante.

##### - pH:

<img title="a title" alt="Alt text" src="images/sensor_ph.jpeg" width="300px">

- No se ve mucha histéresis. Hay harta variación en la calibración pero al recalibrar los sensores vuelven a funcionar.
- Se esperar hacer más experimento para corroborar datos y además poder ir estimando que tan rápido se descalibran los datos, y cuánto se va perdiendo de presición con cada recalibración.

##### - Nivel de Agua:

<img title="a title" alt="Alt text" src="images/sensor_presion.png" width="200px">
<img title="a title" alt="Alt text" src="images/sensor_presion_atm.png" width="200px">

- Para medir el nivel de una columna de agua se usan dos sensores: uno en el fondo del pozo y otro en la superficie para corregir las variaciones en la presión atmosférica que también siente el sensor sumergido. 
- Experimentos fueron positivos, el error de medición fue menor a 1 cm en diferentes experimentos y luego de 3 meses de medición continua equipo sigue midiendo correctamente, no se observa desviación en su medición.

<img title="a title" alt="Alt text" src="images/sensor_presion_experimento1_1.jpeg" width="300px">
<img title="a title" alt="Alt text" src="images/sensor_presion_experimento1_2.jpeg" width="300px">
<img title="a title" alt="Alt text" src="images/sensor_presion_experimento1_0.png" width="300px">

##### - Turbidez:

<img title="a title" alt="Alt text" src="images/sensor_turbidez.png" width="200px">

- Sensores son muy sensibles a la luz, entonces mediciones varían ampliamente dependiendo de la luz ambiente y la posición en que se coloquen, cualquier movivmiento o cambio de alguna de estas condiciones afectará la medición.
- Errores del rango de ~1000 NTU. No confiables, quizás solo apra alertas grandes pero mejor seguir buscando.

<!--
## Aprendizajes
- tener un buen setup del experimento
-->