---
layout: default
title: Proyecto CNC 
nav_order: 9
---

# CNC con lápiz 3D

## Arquitectura de la CNC

Para este proyecto se está realizando una **CNC cartesiana de 3 ejes**, tomando como referencia la CNC documentada en el siguiente sitio:

[Referencia CNC - Huber Girón](https://hubergiron.github.io/cnc/)

La máquina trabaja con los ejes **X, Y y Z**, los cuales permiten controlar la posición de la herramienta.

- **Eje X:** movimiento horizontal.
- **Eje Y:** movimiento hacia adelante y hacia atrás.
- **Eje Z:** movimiento vertical de la herramienta.

En nuestro proyecto se modificará la herramienta original de la CNC. En lugar de utilizar un lápiz convencional, se colocará un **lápiz 3D**, con el objetivo de depositar filamento siguiendo una trayectoria.

Los ejes X y Y serán utilizados para realizar la forma de la figura, mientras que el eje Z permitirá subir el lápiz entre cada una de las capas.

---

## Materiales y componentes

Para realizar la CNC se utilizarán los siguientes materiales y componentes:

- Arduino UNO.
- CNC Shield V3.
- Drivers A4988.
- Motores paso a paso NEMA 17.
- Fuente de alimentación.
- Cable USB.
- Perfil de aluminio 2020.
- Banda dentada GT2.
- Husillo.
- Piñón y cremallera.
- Tornillos y elementos de unión.
- Computadora.
- Lápiz 3D.
- Filamento para lápiz 3D.

### Imágenes de los materiales

> **Espacio para fotografías de los materiales utilizados**

<!-- Agregar aquí una o varias fotografías de los materiales -->

---

## Sistema mecánico

La CNC utiliza **motores paso a paso NEMA 17** para generar el movimiento de los diferentes ejes.

Como los motores producen un movimiento rotativo, se utilizan diferentes mecanismos para convertirlo en un desplazamiento lineal.

La CNC de referencia utiliza diferentes mecanismos dependiendo del eje:

- **Eje X:** banda dentada GT2.
- **Eje Y:** husillo.
- **Eje Z:** sistema de piñón y cremallera.

El eje X utiliza una banda porque permite realizar movimientos rápidos en una estructura ligera. El eje Y utiliza un husillo para obtener un movimiento más controlado y estable. Finalmente, el eje Z utiliza un sistema de piñón y cremallera para subir y bajar la herramienta.

---

## Adaptación del lápiz 3D

Una de las principales modificaciones realizadas al diseño original fue sustituir el lápiz convencional por un **lápiz 3D**.

El lápiz debe quedar colocado de manera firme sobre el eje Z para evitar movimientos durante el funcionamiento de la máquina.

A diferencia de un lápiz normal, el lápiz 3D deposita filamento, por lo que se debe considerar tanto la velocidad de movimiento como la altura entre las diferentes capas.

En nuestro proyecto cada capa tendrá aproximadamente **1 mm de altura**, por lo que después de terminar una vuelta de la figura el eje Z deberá subir 1 mm antes de comenzar la siguiente.

De esta forma, la CNC no solamente dibujará una trayectoria, sino que irá formando una figura mediante varias capas de filamento.

---

## Estructura de la CNC

La estructura de la máquina se basa en **perfil de aluminio 2020**, lo que permite tener una construcción modular y realizar ajustes en los diferentes ejes.

También se utilizan guías y soportes que permiten mantener los movimientos de los carros de forma recta.

Es importante diferenciar entre las guías y los mecanismos de transmisión:

- Las **guías** mantienen el movimiento en una trayectoria recta.
- La **banda, el husillo y la cremallera** son los mecanismos que generan el desplazamiento.

Esta estructura permite que los tres ejes puedan trabajar de manera independiente y posteriormente coordinarse mediante el programa de control.

---

# Hardware

Para controlar los movimientos de la CNC se utilizan principalmente un **Arduino UNO, CNC Shield V3, drivers A4988 y motores NEMA 17**.

El Arduino UNO funciona como el controlador principal de la CNC y ejecuta el firmware GRBL.

Sobre el Arduino se coloca la **CNC Shield V3**, la cual permite conectar los drivers y los motores correspondientes a los ejes X, Y y Z.

Los **drivers A4988** se encargan de controlar los motores paso a paso y permiten configurar el microstepping para obtener movimientos más suaves y precisos.

Los motores NEMA 17 se conectan a las salidas correspondientes de cada eje y son los encargados de realizar físicamente los movimientos de la CNC.

La alimentación de los motores se realiza mediante una fuente externa, mientras que el Arduino se conecta a la computadora mediante un cable USB para cargar GRBL y comunicarse con el software de control.

---

# Software

Para configurar y controlar la CNC se utilizan principalmente:

- **Arduino IDE**
- **GRBL 1.1**
- **OpenBuilds CONTROL**

## Arduino IDE

Arduino IDE se utiliza para cargar el firmware **GRBL** al Arduino UNO.

Primero se conecta el Arduino mediante USB y se selecciona la placa **Arduino UNO** y el puerto correspondiente.

Después se instala la librería de GRBL y se abre el ejemplo:

`Archivo → Ejemplos → grbl → GrblUpload`

Finalmente se carga el programa al Arduino.

---

## GRBL

**GRBL** es el firmware encargado de interpretar las instrucciones G-code y convertirlas en señales para controlar los motores de los ejes X, Y y Z.

Gracias a GRBL, el Arduino puede recibir comandos desde la computadora y ejecutar los movimientos correspondientes de la CNC.

También permite configurar parámetros importantes como la velocidad, aceleración y los pasos por milímetro de cada eje.

---

## OpenBuilds CONTROL

Después de instalar GRBL se utiliza **OpenBuilds CONTROL** para comunicarse con la CNC.

Este programa permite:

- Conectarse con el Arduino.
- Mover manualmente los ejes.
- Comprobar el sentido de los motores.
- Configurar parámetros de GRBL.
- Cargar archivos G-code.
- Ejecutar las trayectorias de la CNC.

Antes de comenzar con la impresión se realizan movimientos pequeños de prueba en los tres ejes para comprobar que X, Y y Z funcionen correctamente.

Posteriormente se utilizará este programa para cargar la trayectoria que seguirá el **lápiz 3D** y realizar las pruebas de impresión.