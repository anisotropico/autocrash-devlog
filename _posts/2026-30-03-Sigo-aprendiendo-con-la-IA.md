---
layout: post
title: "Continuamos con la IA"
subtitle: "Surgen dudas, problemas, y muchas otras cosas"
date: 2026-03-30
tags: [meta, +IA]
---

El sistema empieza a tomar forma. (Despacio, que es un poco "denso")

## Sensores

La base ya estaba bien definida:

- 6 rayos por agente.
    - frontal
    - 30 grados izquierda y derecha
    - 90 grados izquierda y derecha
    - trasero
- 4 canales por rayo. 
    - Distancia a pared
    - Distancia a coche
    - Orientación del coche
    - Distancia a peatón

Un sistema compacto pero suficientemente expresivo para describir el entorno inmediato.

## Determinismo y colisiones

El primer problema serio apareció en la física coche-coche.

El resultado dependía del orden de procesamiento.  
Eso introduce indeterminismo. Y el indeterminismo rompe cualquier sistema de aprendizaje.

La solución fue externalizar completamente la interacción entre coches:

- Particionado espacial en grid.
- Tres fases claras:
  1. Asignación a celdas.
  2. Detección sobre snapshot.
  3. Resolución conjunta.

Esto no solo estabiliza el sistema.  
También mejora rendimiento.

## Hull físico

Un hull basado en 6 esferas.

Suficiente para capturar volumen sin complicar la detección.

El punto de contacto preciso permite calcular torque de forma natural:

torque = brazo de palanca × fuerza

Sin diseñarlo explícitamente, aparece un comportamiento tipo *spin arcade*.

Física simple, resultado visualmente atractivo y divertido.

## Aprendizaje por imitación

Se introduce un sistema de *learning from demonstration*:

- Se registran y graban pares (sensores, steering) del jugador humano.
- Se añade backpropagation a una red que inicialmente solo tenía forward pass. (Recordemos que era evolutiva)
- El genoma entrenado se inyecta en la población evolutiva.

Esto acelera el arranque del sistema.

No parte de ruido.  
Parte de intención.

## Curriculum learning

Aparece el siguiente problema: demasiada información desde el inicio.

La red no converge.

La solución es sorprendentemente simple:

Un único parámetro que controla la complejidad del mundo percibido.

- Inicialmente: el coche solo “ve” paredes.
- Progresivamente: se activan coches y peatones.

Implementación:

Un lerp sobre los canales de entrada.

Solo se ajusta lo que el agente percibe. Pero poco a poco (similar al aprendizaje humano)

## Evolución de la red

Se introduce profundidad en la red:

26 → 16 → 8 → 1

No por tamaño, sino por jerarquía:

- Primera capa: detección de patrones sensoriales.
- Segunda capa: decisión.

Se separa percepción de acción.

## Conclusión

El sistema empieza a comportarse como algo más que un conjunto de reglas.

Hay:

- Sensores coherentes.
- Física determinista.
- Representación estable.
- Aprendizaje guiado.
- Complejidad progresiva.

Creo que tendré que hacer muchas, muchas más cositas. (Es lo que tiene aprender a construir IA)