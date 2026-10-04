---
layout: default
title: Brazo robot
nav_order: 6
---
# Brazo Robot
## Semana 5 y 6 

En este proyecto se realizó un brazo robótico de 3 grados de libertad con una pinza, utilizando servomotores, Arduino y potenciómetros para controlar cada uno de sus movimientos.
El objetivo  del proyecto fue diseñar, construir y programar un brazo robótico capaz de moverse mediante potenciómetros y utilizar una pinza para tomar una pelota de aproximadamente de **6cm de diámetro**
La estructura del brazo se realizó utilizando **MDF de 3 mm**, cortado en la cortadora láser. También se realizaron las conexiones electrónicas necesarias para controlar los servomotores mediante un Arduino.

---


# Materiales

Los materiales utilizados para la realización del brazo robótico fueron:

| Material | Cantidad  | Uso |
|---|---:|---|
| Arduino | 1 | Controlar los servomotores y recibir la señal de los potenciómetros |
| Servomotores SG90 | 4 | Realizar los movimientos del brazo y de la pinza |
| Potenciómetros 1kOhms | 4 | Controlar manualmente la posición de cada servomotor |
| Protoboard | 1 | Realizar las conexiones del circuito |
| Cables jumper | Varios | Conectar los componentes |
| Cable USB A-B | 1 | Programar y alimentar el Arduino |
| MDF de 3 mm | Según diseño | Fabricar la estructura del brazo |
| Tornillos y tuercas | Varios | Unir algunas partes de la estructura |


![Materiales](assets/img/05-brazorobot/PicMateriales.png)

<p align="center"><em>Materiales utilizados </em></p>
---

# Diseño del brazo

## Primer intento en SOLIDWORKS

Inicialmente se intentó realizar desde cero el diseño completo del brazo utilizando **SOLIDWORKS**.

La idea era diseñar cada una de las piezas de la estructura tomando en cuenta las medidas de los servomotores, los puntos de unión y el tamaño máximo permitido para el brazo.
Sin embargo, durante este proceso se presentaron varios problemas para conseguir que todas las piezas coincidieran correctamente entre sí y que el ensamble completo funcionara como se esperaba.

![Solidworks](assets/img/05-brazorobot/solidwoks.png)

<p align="center"><em>Diseños de Solidworks.</em></p>


---

# Plantilla utilizada

Debido a que el diseño realizado inicialmente en SOLIDWORKS no funcionó como se esperaba, se utilizó una **plantilla externa** como base para fabricar las piezas del brazo.

La plantilla utilizada fue la siguiente:


![Plantilla 1](assets/img/05-brazorobot/Plantilla1.png)

<p align="center"><em>Figura 1. Plantillas de las piezas (parte 1) .</em></p>


![Plantilla 2](assets/img/05-brazorobot/Plantilla2.png)

<p align="center"><em>Figura 2. Plantillas de las piezas (parte 2) .</em></p>


Antes de mandar las piezas a corte láser, el diseño se ajustó para trabajar con **MDF de 3 mm de grosor**, ya que este era el material disponible para realizar la estructura.


---

# Corte láser

Una vez que se tuvo el diseño final, las piezas se acomodaron para aprovechar de mejor manera el espacio disponible en la placa de MDF.
Se verificó que el archivo tuviera las dimensiones correctas y que estuviera preparado para trabajar con un material de **3 mm de grosor**.
Después se llevó el archivo a la cortadora láser para realizar el corte de cada una de las piezas.

**Video del corte:**  
<video width="700" controls>
  <source src="{{ 'assets/videos/03-arduino/04-brazorobot/cortadoralaser.mp4' | relative_url }}" type="video/mp4">
</video>


---
# Ensamble del brazo

Después de tener todas las piezas se comenzó con el ensamble del brazo robótico siguiendo un manual con instrucciones el cual fue el siguiente:

**Instrucciones del armado :**  
[Ver Instrucciones](https://es.slideshare.net/slideshow/instrucciones-armarbrazorobotico/147417473#google_vignette)

Primero se armó la base y posteriormente se fueron agregando los diferentes soportes, brazos y servomotores.
Durante el ensamble se tuvo que revisar constantemente que las piezas pudieran moverse libremente y que los servomotores no chocaran con la estructura.

Los servomotores SG90 fueron colocados en diferentes partes del brazo para controlar:

1. Movimiento de la base.
2. Movimiento del brazo inferior.
3. Movimiento del brazo superior.
4. Apertura y cierre de la pinza.

---

# Circuito electrónico

Para controlar el brazo se utilizó un **Arduino**, cuatro potenciómetros y cuatro servomotores SG90.
Cada potenciómetro se encarga de controlar un movimiento diferente del brazo. Al girar un potenciómetro, Arduino lee su valor y lo convierte en un ángulo que posteriormente se manda al servomotor correspondiente.

Las conexiones utilizadas fueron:

| Parte | Servo | Potenciómetro |
|---|---|---|
| Base | Pin digital 3 | A0 |
| Brazo inferior | Pin digital 5 | A1 |
| Brazo superior | Pin digital 6 | A2 |
| Pinza | Pin digital 9 | A3 |

El Arduino fue conectado mediante un **cable USB A-B**, utilizado tanto para cargar el programa como para realizar las primeras pruebas del circuito.

Primero se realizó un modelo en Tinkercad para simular el circuito con el código para posteriormente realizar las conexiones en físico.

![Circuito](assets/img/05-brazorobot/picArduino.png)

<p align="center"><em>Circuito realizado en Tinkercad .</em></p>


---

# Programación

Para controlar los servomotores se utilizó la librería `Servo.h` de Arduino y el programa para usar el código fue el de Arduino IDE.

El programa lee el valor de cada potenciómetro utilizando las entradas analógicas del Arduino. Como los potenciómetros entregan valores entre 0 y 1023, estos valores se convierten a un rango aproximado entre 0° y 180° para controlar la posición de cada servomotor.

El código utilizado fue el siguiente:


![Código1](assets/img/05-brazorobot/Codigo1.jpg)
![Código2](assets/img/05-brazorobot/Codigo2.jpg)
![Código3](assets/img/05-brazorobot/Codigo3.jpg)

<p align="center"><em>Código usado para el funcionamiento.</em></p>

---
# Videos del funcionamiento del brazo robótico


**Video del  brazo robótico funcionando:**  
<video width="700" controls>
  <source src="{{ 'assets/videos/03-arduino/04-brazorobot/videoRobotSolo.mp4' | relative_url }}" type="video/mp4">
</video>


**Video del  brazo robótico pasandole la pelota a otro brazo:**  
<video width="700" controls>
  <source src="{{ 'assets/videos/03-arduino/04-brazorobot/videoRobot2.mp4' | relative_url }}" type="video/mp4">
</video>

