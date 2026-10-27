---
layout: default
title: Impresión 3D
nav_order: 8
---

# Diseño e impresión 3D

## Introducción

En esta práctica diseñé un fidget toy en Autodesk Fusion y una figura fija de Darth Vader utilizando la IA de MakerLab. La intención fue conocer el proceso desde el diseño hasta la impresión, además de comparar el mismo fidget toy en dos impresoras diferentes.

## Objetivo

Crear una figura con al menos dos piezas móviles y otra diseñada con IA de máximo 5 × 5 cm, documentando el proceso y los resultados de impresión.

## Materiales y herramientas

- Autodesk Fusion.
- MakerLab de MakerWorld.
- Impresora Creality CR-10 SE.
- Impresora Creality Ender-3 V3 KE.
- Filamento: PLA (blanco y rojo).

---

## 1. Diseño del fidget toy

El diseño se realizó en **Autodesk Fusion**, siguiendo este [video tutorial](https://www.youtube.com/watch?v=n7AkvIi4th4&t=35s).

### Bocetos iniciales

Primero dibujé el hexágono de referencia y después el perfil de las piezas. En el perfil utilicé un espesor de **1.2 mm**, una altura de **10 mm** y un ángulo de **130°**.

![Boceto inicial](assets/img/07-impresion3d/part1fidget.png)

![Perfil con medidas](assets/img/07-impresion3d/parte2fidget.png)

### Extrusión y patrón rectangular

Realicé una extrusión de **50 mm hacia cada lado**. Después apliqué un patrón rectangular de **30 repeticiones**, con un espaciado de **1.2 + 0.6 = 1.8 mm**. Los 0.6 mm corresponden a la separación considerada entre las piezas.

![Extrusión](assets/img/07-impresion3d/part3fidget.png)

![Patrón rectangular](assets/img/07-impresion3d/part4fidget.png)

### Corte y patrón circular

Realicé una extrusión inversa con la operación de corte para retirar el material sobrante. Después utilicé un patrón circular de **6 repeticiones alrededor del eje Z**, identificado en azul, para completar el hexágono.

![Corte](assets/img/07-impresion3d/part5fidget.png)

![Patrón circular](assets/img/07-impresion3d/part6fidget.png)

### Diseño terminado

Con estas operaciones obtuve el modelo completo del fidget toy.

![Diseño terminado](assets/img/07-impresion3d/part7fideget.png)

![Otra vista del diseño](assets/img/07-impresion3d/part8fidget.png)

---

## 2. Impresión y comparación del fidget toy

La primera impresión se realizó en una **Creality CR-10 con soportes automáticos**. En la segunda impresión del mismo diseño **no se utilizaron soportes**.

![Primera impresión](imagenes/fidget-impresion-1.jpg)

![Segunda impresión](imagenes/fidget-impresion-2.jpg)

| Característica | Creality CR-10 | Segunda impresora: [modelo] |
|---|---|---|
| Material | [Completar] | [Completar] |
| Dimensiones | [Completar] | [Completar] |
| Altura de capa | [Completar] | [Completar] |
| Relleno | [Completar] | [Completar] |
| Soportes | Automáticos | Sin soportes |
| Tiempo | [Completar] | [Completar] |
| Acabado y movimiento | [Completar] | [Completar] |

**¿Cuál fue más rápida?**  
[Completar con los tiempos y la diferencia entre ambas].

**¿Cuál tuvo mejor resultado y por qué?**  
[Comparar el acabado, el retiro de soportes y el movimiento de las piezas].

La diferencia en el uso de soportes y los demás ajustes se tomará en cuenta al comparar los resultados.

---

## 3. Figura fija con IA: Darth Vader

Para esta figura utilicé **MakerLab de MakerWorld**. Cargué una imagen de Darth Vader y la IA generó el modelo 3D, del cual obtuve el archivo STL.

### Imagen de referencia y modelo generado

![Imagen de referencia](assets/img/07-impresion3d/modelodarth.png)

![Modelo generado en MakerLab](assets/img/07-impresion3d/markerlabdarth.png)

### Preparación e impresión

Preparé el modelo para imprimirlo en una **Creality CR-10 SE**, utilizando **soportes automáticos**. El límite indicado para esta figura es de **5 × 5 cm**.

| Dato | Información |
|---|---|
| Dimensiones finales | [Completar ancho, fondo y alto] |
| Material | [Completar] |
| Altura de capa | [Completar] |
| Relleno | [Completar] |
| Soportes | Automáticos |
| Tiempo de impresión | [Completar] |

![Preparación y medidas](imagenes/vader-preparacion.png)

![Proceso de impresión](imagenes/vader-impresion.jpg)

Después de imprimir se retiraron los soportes para revisar el acabado de la figura.

**Observaciones:** [Describir los detalles de la cara, el casco y cualquier dificultad al retirar los soportes].

---

## 4. Resultados finales

### Fidget toys

![Fidget toy de la Creality CR-10](imagenes/fidget-resultado-1.jpg)

![Fidget toy de la segunda impresora](imagenes/fidget-resultado-2.jpg)

### Darth Vader

![Darth Vader terminado](imagenes/vader-resultado.jpg)

![Otra vista de Darth Vader](imagenes/vader-resultado-2.jpg)

---

## 5. Videos

- [Impresión en Creality CR-10 SE](assets/videos/07-impresio3d/videocrealitylabdemario.mp4).
- [Movimiento de los fidget toys](assets/videos/07-impresio3d/fidgettoy.mp4).

---

## Conclusión

Esta práctica me ayudó a entender cómo pasar de un diseño digital a una pieza impresa. En Fusion trabajé con bocetos, extrusiones y patrones, mientras que con MakerLab pude generar una figura a partir de una imagen usando IA.

También fue importante considerar la separación entre las piezas móviles y el uso de soportes. La comparación de las impresiones permitió identificar cuál tuvo mejor acabado, menor tiempo y mejor movimiento de las piezas.

## Referencias

- [Tutorial del fidget toy](https://www.youtube.com/watch?v=n7AkvIi4th4&t=35s).
- Autodesk Fusion: software de diseño.
- MakerLab de MakerWorld: generación del modelo con IA.