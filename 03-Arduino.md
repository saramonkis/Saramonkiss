---
layout: default
title: Arduino
nav_order: 4
---

# Semana 2

**Arduino**
 
Arduino es una plataforma electrónica de código abierto compuesta por una placa programable y un programa llamado Arduino IDE. Su principal objetivo es facilitar la creación de proyectos relacionados con la electrónica, la programación y la robótica.

La placa Arduino contiene un microcontrolador, el cual funciona como el “cerebro” del circuito. Este componente recibe información por medio de sus entradas, procesa las instrucciones del programa y genera una respuesta mediante sus salidas. Por ejemplo, Arduino puede detectar cuando se presiona un botón y, como respuesta, encender un LED, mover un motor o activar una alarma. (Educ.ar, 2021)

![Arduino][img 1]

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


[img 1]: <assets/img/03-arduino/arduino .png>
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

![Cable USB](assets/img/semana2/cable-usb.jpg)

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