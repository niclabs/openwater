# 📦 Submersible case

> Any questions you can write us at: openwater@niclabs.cl

### Prototype and tests

Details on the design and construction of the system's submersible casing in its current version are presented below. Tests have been carried out in a controlled environment (laboratory) by immersing the casing in water tanks for different periods of time and evaluating the effectiveness in protecting the interior according to the degree of IP protection achieved (international standard CEI 60529 Degrees of Protection).

A first prototype was manufactured to carry out tests with the pressure sensors (water level) to submerge them in a well of about ~5 meters. Generic plumbing materials were used and it was filled with rice to absorb moisture in case of leaks.

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_primera_version_2.png" width="200px">
<img title="a title" alt="Alt text" src="images/carcasa_primera_version.jpeg" width="300px"></p>

This prototype was submerged for about 45 minutes and when it was removed it did have enough moisture inside, but it did not have a "water well", the moisture was enough to damage the electronics over time. It is believed that the leaks were from the covers of the pressure sensors.xzx

A new version of the casing is designed, now adding the requirements of prioritizing accessible and available materials in the local market. The initial geometry contemplates a transparent acrylic tube, covers and an internal support for the electronics, as well as lateral spaces for the output of the sensors and UTP cable. The side covers make the total seal of the device in this version, by means of o'rings and fixing to the internal support, which is what will keep the covers under pressure inside the system, generating the desired IP69 protection.

<p align="center"><img title="a title" alt="Alt text" src="images/Nodo completo.JPG" width="600px"></p>

Different tests of the new prototype are carried out, both to the sealing components of the sensors and to the complete equipment in a controlled environment made up of a 6 meter high PVC pipe to simulate the pressure of a column of water.

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_prototipo_1.jpg" width="300px"></p>

Finally, and after some iterations, a leak-free system was achieved, as observed in the photo below :).

This ptototype is then tested in a well in the Laguna Caren sector, here tests were carried out by submerging it progressively to greater depths (10, 20, 30 and 40mt).

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_validacion_1.jpg" width="300px"></p>

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_validacion_2.jpg" width="300px"></p>

The results were positive and the sealing was successful, achieving IP68 protection. There are slight leaks that are being checked after a long time depending on how the case is covered so it is not classified as ip69 yet.

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_validacion_3.jpg" width="300px"></p>

### Communications cable

In addition to the housing, the communication cable between the underwater data capture module and the surface communication module was designed. To do this, a UTP cable is used inside a hose to prevent corrosion. The focus was on achieving low cost, which was successfully achieved at less than half the cost of commercial versions. This cable is responsible for transporting the data between the capture module and the communication module.

<p align="center">
<img title="a title" alt="Alt text" src="images/carcasa_cable_manguera.png" height="250px">
<img title="a title" alt="Alt text" src="images/carcasa_cable_union.png" height="250px">
</p>

### Results

The equipment, or data capture module, once fully assembled has a cylindrical shape of a **size** of 55 cm long and 6.3 cm in radius.

<p align="center"><img title="a title" alt="Alt text" src="images/tamaño_equipo_captura.png" width="600px"></p>

The **cost** of materials follows from the case and the communication cable. The communication cable can vary in length depending on the application, we assume the longest length of 50 meters for estimation.

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_costos.png" width="400px"></p>

A degree of **IP protection** IP66 is achieved but partially, the casing does not have a reliable behavior and iteration on the design is pending.

### Relevant files

#### List of Materials and instructions

More detail on the list of materials and assembly instructions for the casing can be found in the assembly manual:

- [Manual armado carcasa v2 - 2022 Feb](https://github.com/niclabs/openwater/blob/main/3.%20Carcasa/Manual%20armado%20carcasa%20v2%20-%202022Feb.pdf)

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_listamateriales.png" width="500px"></p>

#### Design and fabrication

Design files, materials and instructions can be found at the following link.

- [/niclabs/openwater/2. Carcasa](https://github.com/niclabs/openwater/tree/main/3.%20Carcasa)

<p align="center"><img title="a title" alt="Alt text" src="images/carcasa_planos_placa.png" width="220px"><img title="a title" alt="Alt text" src="images/carcasa_planos_tapa_sup.png" width="220px"><img title="a title" alt="Alt text" src="images/carcasa_planos_tapa_inf.png" width="220px"></p>
