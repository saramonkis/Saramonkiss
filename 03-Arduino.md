---
layout: default
title: Arduino
nav_order: 4
---
# Arduino
# Semana 2 y 3 

**Arduino**
 
Arduino es una plataforma electrónica de código abierto compuesta por una placa programable y un programa llamado Arduino IDE. Su principal objetivo es facilitar la creación de proyectos relacionados con la electrónica, la programación y la robótica.

La placa Arduino contiene un microcontrolador, el cual funciona como el “cerebro” del circuito. Este componente recibe información por medio de sus entradas, procesa las instrucciones del programa y genera una respuesta mediante sus salidas. Por ejemplo, Arduino puede detectar cuando se presiona un botón y, como respuesta, encender un LED, mover un motor o activar una alarma. (Educ.ar, 2021)

![Arduino](assets/img/03-arduino/arduino .png)

**¿Cómo se utiliza Arduino?**

1. Conectar la placa Arduino a la computadora mediante un cable USB.
2. Abrir el programa Arduino IDE.
3. Seleccionar **Herramientas > Placa > Arduino Uno**.
4. Seleccionar el puerto donde está conectado el Arduino.
5. Escribir o pegar el código del circuito.
6. Presionar el botón de verificación para revisar errores.
7. Presionar el botón de carga para enviar el código al Arduino.
8. Comprobar que el circuito funcione correctamente.

[Sitio de información][info1]
[Sitio de información][info2]



[info2]: https://intef.es/observatorio_tecno/arduino-tecnologia-y-creatividad-en-tus-manos/
[info1]: https://www.educ.ar/recursos/156851/conoce-arduino-una-introduccion-a-la-programacion-y-la-robot

Materiales utilizados 

| Material | Cantidad | Descripción |
|:---------|:--------:|:------------|
| Arduino Uno | 1 | Es la placa principal que recibe y ejecuta el código de cada circuito. |
| Protoboard | 1 | Permite conectar los componentes sin tener que soldarlos. |
| Cable USB tipo A-B | 1 | Conecta el Arduino a la computadora, proporciona energía y permite cargar el código. |
| Cables jumper | Varios | Se utilizan para realizar las conexiones entre el Arduino, la protoboard y los demás componentes. |
| LEDs rojos | 5 o más | Emiten luz cuando reciben corriente eléctrica y sirven como indicadores visuales. |
| Resistencias de 220 Ω o 330 Ω | Varias | Limitan la corriente que reciben los LEDs para evitar que se dañen. |
| Resistencias de 10 kΩ | 2 | Mantienen estable la señal de entrada de los botones y evitan lecturas incorrectas. |
| Botones pulsadores | 2 | Funcionan como interruptores momentáneos y envían una señal cuando son presionados. |
| Potenciómetro | 1 | Es una resistencia variable. Al girar su perilla cambia el valor de la señal que recibe el Arduino. |
| Microservomotor SG90 | 1 | Es un motor pequeño cuyo ángulo puede controlarse mediante una señal enviada por Arduino. |
| Display digital de 7 segmentos | 1 | Está formado por siete pequeños segmentos luminosos que permiten mostrar números del 0 al 9. |

---
## Arduino Uno

El Arduino Uno es la placa principal de los circuitos. Recibe las señales de entrada, ejecuta el código y controla los componentes conectados a sus pines.

![Arduino Uno](assets/img/03-arduino/arduino .png)

<p align="center"><em>Figura 1. Placa Arduino Uno utilizada en los circuitos.</em></p>

## Protoboard

La protoboard es una placa de pruebas que permite conectar componentes electrónicos sin soldarlos. Sus orificios internos están unidos en grupos para facilitar las conexiones.

![Protoboard](assets/img/03-arduino/protoboard.jpg)

<p align="center"><em>Figura 2. Protoboard utilizada para montar los circuitos.</em></p>

## Cable USB tipo A-B

Este cable conecta el Arduino Uno con la computadora. Sirve para alimentar la placa y cargar los programas realizados en Arduino IDE.

![Cable USB](assets/img/03-arduino/cableusb.jpg)

<p align="center"><em>Figura 3. Cable USB utilizado para conectar el Arduino.</em></p>

## Cables jumper

Los cables jumper permiten unir los pines del Arduino con los componentes colocados en la protoboard. Se utilizaron cables de diferentes colores para distinguir las conexiones.

![Cables jumper](assets/img/03-arduino/jumpers.jpg)

<p align="center"><em>Figura 4. Cables jumper utilizados en las conexiones.</em></p>

## LEDs

Los LEDs son diodos que producen luz cuando la corriente circula en la dirección correcta. La pata larga es el positivo o ánodo y la corta es el negativo o cátodo.

![LEDs](assets/img/03-arduino/leds.jpg)

<p align="center"><em>Figura 5. LEDs utilizados como indicadores visuales.</em></p>

## Resistencias

Las resistencias limitan el paso de corriente eléctrica. Las de 220 Ω o 330 Ω protegen los LEDs, mientras que las de 10 kΩ ayudan a mantener estable la lectura de los botones.

![Resistencias](assets/img/03-arduino/resisitencias.jpg)

<p align="center"><em>Figura 6. Resistencias utilizadas en los circuitos.</em></p>

## Botones pulsadores

Los botones pulsadores funcionan como interruptores momentáneos. Cuando se presionan cierran el circuito y envían una señal al Arduino; al soltarlos regresan a su estado original.

![Botones](assets/img/03-arduino/pulsador.jpg)

<p align="center"><em>Figura 7. Botones pulsadores utilizados como entradas.</em></p>

## Potenciómetro

El potenciómetro es una resistencia variable de tres terminales. Al girar su perilla cambia el voltaje de salida, permitiendo controlar valores como la posición del servomotor.

![Potenciómetro](assets/img/03-arduino/Potentiometer.jpg)

<p align="center"><em>Figura 8. Potenciómetro utilizado para controlar el servomotor.</em></p>

## Microservomotor SG90

El microservomotor SG90 es un motor pequeño que puede colocarse en diferentes ángulos. Cuenta con tres conexiones: alimentación, tierra y señal de control.

![Microservomotor SG90](assets/img/03-arduino/servo.jpg)

<p align="center"><em>Figura 9. Microservomotor utilizado en uno de los circuitos.</em></p>

## Display digital de 7 segmentos

El display de 7 segmentos está formado por siete secciones luminosas identificadas con las letras de la **A** a la **G**. Arduino enciende diferentes combinaciones de segmentos para representar los números del 0 al 9. Algunos modelos también incluyen un punto decimal.

![Display de 7 segmentos](assets/img/03-arduino/display.jpg)

<p align="center"><em>Figura 10. Display digital de 7 segmentos.</em></p>

----

## 1_Arduino Básico Salidas Digitales

# Descripción

En esta primera sección se trabajó con las salidas digitales del Arduino. Estas salidas permiten enviar señales de encendido y apagado para controlar componentes como LEDs y el display de 7 segmentos. Los circuitos de este apartado van del número 0 al 9.

---

## Circuito 0

![Circuito 0 en Tinkercad]({{ '/assets/img/03-arduino/0-0.png' | relative_url }})

<p align="center"><em>Imagen del circuito 0 realizado en Tinkercad junto con su código.</em></p>

![Circuito 0 físico]({{ '/assets/img/03-arduino/foto0y1.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 0 y 1.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 0.</em></p>

---

## Circuito 1

![Circuito 1 en Tinkercad]({{ '/assets/img/03-arduino/1-1.png' | relative_url }})

<p align="center"><em>Imagen del circuito 1 realizado en Tinkercad junto con su código.</em></p>

![Circuito 1 físico]({{ '/assets/img/03-arduino/foto0y1.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 0 y 1.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 1.</em></p>

---

## Circuito 2

![Circuito 2 en Tinkercad]({{ '/assets/img/03-arduino/1-2.png' | relative_url }})

<p align="center"><em>Imagen del circuito 2 realizado en Tinkercad junto con su código.</em></p>

![Circuito 2 físico]({{ '/assets/img/03-arduino/foto 2y3.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 2 y 3.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 2.</em></p>

---

## Circuito 3

![Circuito 3 en Tinkercad]({{ '/assets/img/03-arduino/1-3.png' | relative_url }})

<p align="center"><em>Imagen del circuito 3 realizado en Tinkercad junto con su código.</em></p>

![Circuito 3 físico]({{ '/assets/img/03-arduino/foto 2y3.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 2 y 3.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 3.</em></p>

---

## Circuito 4

![Circuito 4 en Tinkercad]({{ '/assets/img/03-arduino/1-4.png' | relative_url }})

<p align="center"><em>Imagen del circuito 4 realizado en Tinkercad junto con su código.</em></p>

![Circuito 4 físico]({{ '/assets/img/03-arduino/foto 4.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 4.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 4.</em></p>

---

## Circuito 5

![Circuito 5 en Tinkercad]({{ '/assets/img/03-arduino/1-5.png' | relative_url }})

<p align="center"><em>Imagen del circuito 5 realizado en Tinkercad junto con su código.</em></p>

![Circuito 5 físico]({{ '/assets/img/03-arduino/foto 5.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 5.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 5.</em></p>

---

## Circuito 6

![Circuito 6 en Tinkercad]({{ '/assets/img/03-arduino/1-6.png' | relative_url }})

<p align="center"><em>Imagen del circuito 6 realizado en Tinkercad junto con su código.</em></p>

![Circuito 6 físico]({{ '/assets/img/03-arduino/foto 6.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 6.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 6.</em></p>

---

## Circuito 7

![Circuito 7 en Tinkercad]({{ '/assets/img/03-arduino/1-7.png' | relative_url }})

<p align="center"><em>Imagen del circuito 7 realizado en Tinkercad junto con su código.</em></p>

![Circuito 7 físico]({{ '/assets/img/03-arduino/foto 7.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 7.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 7.</em></p>

---

## Circuito 8

![Circuito 8 en Tinkercad]({{ '/assets/img/03-arduino/1-8.png' | relative_url }})

<p align="center"><em>Imagen del circuito 8 realizado en Tinkercad junto con su código.</em></p>

![Circuito 8 físico]({{ '/assets/img/03-arduino/foto 8.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 8.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 8.</em></p>

---

## Circuito 9

![Circuito 9 en Tinkercad]({{ '/assets/img/03-arduino/1-9.png' | relative_url }})

<p align="center"><em>Imagen del circuito 9 realizado en Tinkercad junto con su código.</em></p>

![Circuito 9 físico]({{ '/assets/img/03-arduino/foto 9.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 9.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 9.</em></p>

---

## 2_Arduino Básico: Entradas Digitales

# Descripción

En esta sección se utilizaron las entradas digitales del Arduino. Estas entradas reciben información de componentes como los botones pulsadores. Dependiendo de la señal recibida, Arduino puede encender o apagar diferentes LEDs. Los circuitos de este apartado van del número 10 al 16.

---

## Circuito 10

![Circuito 10 en Tinkercad]({{ '/assets/img/03-arduino/1-10.png' | relative_url }})

<p align="center"><em>Imagen del circuito 10 realizado en Tinkercad junto con su código.</em></p>

![Circuito 10 físico]({{ '/assets/img/03-arduino/foto 10y12.png' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 10.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 10.</em></p>

---

## Circuito 11

![Circuito 11 en Tinkercad]({{ '/assets/img/03-arduino/2-11.png' | relative_url }})

<p align="center"><em>Imagen del circuito 11 realizado en Tinkercad junto con su código.</em></p>

![Circuito 11 físico]({{ '/assets/img/03-arduino/foto 11.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 11 y 13.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 11.</em></p>

---

## Circuito 12

![Circuito 12 en Tinkercad]({{ '/assets/img/03-arduino/2-12.png' | relative_url }})

<p align="center"><em>Imagen del circuito 12 realizado en Tinkercad junto con su código.</em></p>

![Circuito 12 físico]({{ '/assets/img/03-arduino/foto 10y12.png' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 12.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 12.</em></p>

---

## Circuito 13

![Circuito 13 en Tinkercad]({{ '/assets/img/03-arduino/2-13.png' | relative_url }})

<p align="center"><em>Imagen del circuito 13 realizado en Tinkercad junto con su código.</em></p>

![Circuito 13 físico]({{ '/assets/img/03-arduino/foto 13.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 11 y 13.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 13.</em></p>

---

## Circuito 14

![Circuito 14 en Tinkercad]({{ '/assets/img/03-arduino/2-14.png' | relative_url }})

<p align="center"><em>Imagen del circuito 14 realizado en Tinkercad junto con su código.</em></p>

![Circuito 14 físico]({{ '/assets/img/03-arduino/foto 14.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 14.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 14.</em></p>

---

## Circuito 15

![Circuito 15 en Tinkercad]({{ '/assets/img/03-arduino/1-15.png' | relative_url }})

<p align="center"><em>Imagen del circuito 15 realizado en Tinkercad junto con su código.</em></p>

![Circuito 15 físico]({{ '/assets/img/03-arduino/foto 15.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 15.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 15.</em></p>

---

## Circuito 16

![Circuito 16 en Tinkercad]({{ '/assets/img/03-arduino/2-16.png' | relative_url }})

<p align="center"><em>Imagen del circuito 16 realizado en Tinkercad junto con su código.</em></p>

![Circuito 16 físico]({{ '/assets/img/03-arduino/foto 16.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 16.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 16.</em></p>

---

## 3_Arduino Básico: Servomotores

# Descripción

En esta sección se trabajó con servomotores. Estos motores permiten controlar su posición mediante ángulos específicos. También se utilizó un potenciómetro para cambiar la posición del servomotor de manera manual. Los circuitos de este apartado van del número 17 al 21.

---

## Circuito 17

![Circuito 17 en Tinkercad]({{ '/assets/img/03-arduino/3-17.png' | relative_url }})

<p align="center"><em>Imagen del circuito 17 realizado en Tinkercad junto con su código.</em></p>

![Circuito 17 físico]({{ '/assets/img/03-arduino/foto 17y18.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 17.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 17.</em></p>

---

## Circuito 18

![Circuito 18 en Tinkercad]({{ '/assets/img/03-arduino/3-18.png' | relative_url }})

<p align="center"><em>Imagen del circuito 18 realizado en Tinkercad junto con su código.</em></p>

![Circuito 18 físico]({{ '/assets/img/03-arduino/foto 17y18.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 18.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 18.</em></p>

---

## Circuito 19

![Circuito 19 en Tinkercad]({{ '/assets/img/03-arduino/3-19.png' | relative_url }})

<p align="center"><em>Imagen del circuito 19 realizado en Tinkercad junto con su código.</em></p>

![Circuito 19 físico]({{ '/assets/img/03-arduino/foto 19.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 19 (2).mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 19.</em></p>

---

## Circuito 19.2

![Circuito 19.2 en Tinkercad]({{ '/assets/img/03-arduino/3-19.2.png' | relative_url }})

<p align="center"><em>Imagen del circuito 19.2 realizado en Tinkercad junto con su código.</em></p>

![Circuito 19.2 físico]({{ '/assets/img/03-arduino/foto 19.2.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/19.2.2.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 19.2 .</em></p>

---

## Circuito 20

![Circuito 20 en Tinkercad]({{ '/assets/img/03-arduino/3-20.png' | relative_url }})

<p align="center"><em>Imagen del circuito 20 realizado en Tinkercad junto con su código.</em></p>

![Circuito 20 físico]({{ '/assets/img/03-arduino/foto 20.jpg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 20.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 20.</em></p>

---

## Circuito 21

![Circuito 21 en Tinkercad]({{ '/assets/img/03-arduino/3-21.png' | relative_url }})

<p align="center"><em>Imagen del circuito 21 realizado en Tinkercad junto con su código.</em></p>

![Circuito 21 físico]({{ '/assets/img/03-arduino/foto 21.jpgg' | relative_url }})

<video width="700" controls>
  <source src="{{ '/assets/videos/03-arduino/video 21.mp4' | relative_url }}" type="video/mp4">
</video>

<p align="center"><em>Imagen y video de la elaboración física del circuito 21.</em></p>

----
## Conclusión 

Durante esta actividad aprendí por primera vez a utilizar Arduino y Arduino IDE para crear diferentes circuitos. Al principio todo se veía un poco complicado por la cantidad de cables, conexiones y líneas de código, pero conforme fui haciendo los ejercicios pude entender mejor para qué servía cada componente y cómo cambiaba el funcionamiento del circuito dependiendo del código que se colocaba.

Primero trabajé con salidas digitales para controlar LEDs y un display de 7 segmentos. Después utilicé entradas digitales, como los botones, para hacer que el Arduino respondiera cuando los presionaba. Finalmente, aprendí a controlar servomotores y a cambiar su posición, lo cual fue de las partes que más me llamó la atención porque pude ver de una manera más clara cómo el código puede producir un movimiento físico.

Hacer primero los circuitos en Tinkercad me ayudó bastante a entender las conexiones y a encontrar algunos errores antes de armarlos físicamente. Aun así, pasar todo a la protoboard real fue un verdadero reto, ya que cualquier cable mal conectado podía hacer que el circuito no funcionara. Aunque en algunos momentos fue un poco frustrante, también fue satisfactorio ver que los circuitos finalmente funcionaban. Con esta práctica comprendí mejor la relación que existe entre el código, las conexiones y los componentes electrónicos, además de que adquirí una idea más clara de todo lo que se puede crear utilizando Arduino.
