---
layout: page
title: Tecnología
subtitle: El Autocrash Engine
permalink: /tecnologia/
---

## Arquitectura del motor

![mixer](../assets/images/Mixer.png)

El nuevo Autocrash no utilizará ningún motor comercial.

Ni Unity, ni Unreal, ni frameworks generalistas.

No es una cuestión ideológica. Es una cuestión de diseño.

Si el proyecto quiere ser un laboratorio real, necesita libertad total. Control absoluto sobre cada decisión técnica. Capacidad de girar rápido cuando una idea lo exija, sin depender de capas externas.

## Motor específico para un único propósito

![mixer2](../assets/images/Mixer2.png)

El motor será desarrollado exclusivamente para Autocrash.

No busca ser genérico ni busca ser reutilizable. 

Busca ser exacto, y permitir que las ideas se construyan sin rodeos innecesarios, sin capas de cebolla, con total libertad.

Una base en C++, portable y desacoplada de cualquier sistema concreto. La lógica del juego estará claramente separada del backend gráfico. El interfaz de render se adaptará a cada entorno sin contaminar el núcleo.

Empezaremos con DirectX por pura comodidad de desarrollo, pero manteniendo desde el inicio una arquitectura que permita sustituir la capa gráfica sin reescribir el corazón del sistema.

### Principios de diseño

![voxel1](../assets/images/imageDetail.jpg)

![voxel2](../assets/images/imageSmoothDetail.jpg)

La representación gráfica estará basada en voxels.

La estética será deliberadamente retro, pero con tecnología contemporánea bajo el capó.

Los coches y personajes estarán voxelizados, preservando la identidad de bloque. Sin embargo, el motor incorporará un sistema propio de suavizado de aristas orientado a mejorar la percepción volumétrica.

No se trata de borrar el voxel, se trata de refinarlo.

La intención es mantener la esencia geométrica eliminando la dureza visual excesiva que suele asociarse al voxel clásico.


---


