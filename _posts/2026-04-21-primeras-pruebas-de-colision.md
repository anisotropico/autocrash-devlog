---
layout: post
title: "Colisión ccohe-coche"
subtitle: "Primeras prubas de colisión"
date: 2026-04-21
tags: [meta, Colisión]
---

Toca abordar el sistema de colisiones entre coches.

Antes de entrar en fuerzas o rotaciones, lo primero es lo rpimero: garantizar una base sólida:

- Detección eficiente.
- Comportamiento determinista.
- Separación estable.

## Representación física

Cada coche se representa mediante un hull de 6 esferas:

- 2 delanteras
- 2 centrales
- 2 traseras

![HullCar]({{ "/assets/images/imagesPosts/SphereHull.png" | relative_url }})

Esto permite:

- Aproximar volumen de forma simple.
- Detectar contactos de manera robusta.
- Obtener puntos de contacto razonables.

Sin complejidad innecesaria.

## Particionado espacial

El grid no almacena esferas.  
Almacena coches.

Cada coche se inserta una única vez por celda.

La asignación a celdas no se hace usando un volumen simple del coche, sino utilizando su representación física:
Un hull de 6 esferas.

Cada esfera:

- Tiene centro y radio.
- Puede ocupar varias celdas.

El coche se inserta en todas las celdas que cubren sus esferas.

## Detección

Dentro de cada celda:

- Se obtienen los coches presentes.
- Se generan pares de coches.
- Para cada par se comprueban todas las combinaciones de sus esferas.

La colisión sigue siendo esfera-esfera.

El grid solo reduce candidatos.

Esto reduce drásticamente el número de comprobaciones.

La detección se basa en:

distancia² < (radio₁ + radio₂)²

Simple y eficiente.

## Snapshot

La detección se realiza sobre un snapshot del estado actual.

Ninguna posición se modifica durante esta fase.

Esto garantiza:

- Determinismo.
- Independencia del orden de iteración.

## Resolución (fase inicial)

Por ahora, el objetivo no es simular física realista.

Solo evitar interpenetración.

Para cada par en colisión:

- Se calcula el vector de separación.
- Se desplazan ambos coches en direcciones opuestas.

```html
<div class="video-container">
  <iframe src="https://youtu.be/3nJ-k8Rw6ms?si=okO4U-tDHzx1ByQW" allowfullscreen></iframe>
</div>
```

## Siguiente paso

Una vez la separación sea estable y consistente, pasaremos al cálculo de fuerzas y torque.