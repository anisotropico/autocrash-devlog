---
layout: post
title: "Orden en el laboratorio"
subtitle: "Primero la estética voxel"
date: 2026-02-18
tags: [meta, estética]
---

Tengo muchas ideas en la cabeza. Es un auténtico hervidero. Aquí dejo algunas:

- Multijugador.  
- Sistemas de voxels tratados como partículas para efectos avanzados.  
- Gran variedad de coches con comportamientos diferenciados.  
- IA capaz de aprender a conducir, hasta el punto de convertirnos en meros observadores (managers) en combates online.

Todo eso es posible.

Pero lo primero es comprobar si la estética voxel realmente funciona para Autocrash.

## Validación antes que expansión

Antes de multijugador, de IA o sistemas complejos, necesito responder a una pregunta básica:

¿Nos gusta cómo se ve?

La identidad visual condicionará todo lo demás. Si la base no convence, cualquier sistema avanzado será irrelevante.

Por eso el siguiente paso no es el juego.  
Es la herramienta.

## El programa de diseño

Llevo tiempo desarrollando un programa propio de creación y animación voxel.

Como siempre, primero construimos la herramienta. Esto no da una sensación de libertad maravillosa. 0 dependencias.

Está desarrollado en Windows MFC con DirectX. Es deliberadamente sencillo, enfocado a dos funciones esenciales:

- Creación de modelos voxel.
- Animación básica.

Nada más. Sin distracciones. (Si nos gusta iremos iterando)

![VoxelEditor]({{ "/assets/images/imagesPosts/VoxelEditor.png" | relative_url }})

## Suavizado de aristas

Uno de los elementos clave ha sido la implementación de un algoritmo propio de suavizado de aristas para geometría voxel.

El objetivo no era eliminar la identidad de bloque, sino aumentar la percepción volumétrica.

El principal reto no fue visual. Fue geométrico.

Controlar la cantidad de geometría generada era crítico. Un suavizado ingenuo multiplica polígonos rápidamente y destruye rendimiento.

El algoritmo actual equilibra:

- Calidad visual.
- Control de densidad geométrica.
- Velocidad de generación.

El resultado es sorprendente.  
La sensación de volumen mejora de forma notable y el sistema funciona a una velocidad muy elevada.

Como vemos en la siguiente imagen, la geometría converge para evitar crecer poligonalmente.

![VoxelChaflan]({{ "/assets/images/imagesPosts/ConvergenciaChaflan.png" | relative_url }})

## Conclusión

Antes de construir el juego, estamos validando la materia prima.

Si la estética voxel suavizada funciona, todo lo demás tendrá sentido.

Si no funciona, es mejor descubrirlo ahora.
