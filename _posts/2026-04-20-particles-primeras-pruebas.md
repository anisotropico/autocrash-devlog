---
layout: post
title: "Partículas"
subtitle: "Partículas en GPU - Decisiones de pipeline"
date: 2026-04-20
tags: [meta, Engine]
---

Cambio de foco.

Sin abandonar la IA, toca subir otras partes del sistema. El desarrollo avanza como un ecualizador: diferentes módulos suben y bajan en intensidad, pero todos evolucionan. Es una cuestión de no consumir todo el foco en una sola parte (son muchas).

## Le toca a las partículas

En versiones anteriores del motor, el sistema de partículas tenía una integración correcta, pero no especialmente sofisticada.

En esta iteración, el objetivo es claro:

Mover todo el sistema a GPU.

- Generación
- Actualización
- Render

Reducir al mínimo la intervención de CPU.

## Geometría vs instanciación

He evaluado dos enfoques:

**1. Geometry Shader**
- Generación dinámica de primitivas (Era el sistema anterior).
- Pipeline compacto.

Problemas:
- Rendimiento irregular en muchos casos.
- Soporte limitado en ciertas plataformas.
- No compatible con entornos como Metal.

**2. Instanciación**
- Un mesh base (quad o similar).
- Transformaciones por instancia.
- Control explícito desde buffers.

Ventajas:
- Más predecible.
- Mejor soporte multiplataforma.
- Escala bien con GPU moderna.
- Más alineado con compute shaders.

Decisión: **instanciación**.

## Integración con compute shaders

El sistema se apoya en compute shaders para:

- Actualizar posición y velocidad.
- Gestionar vida de partículas.
- Preparar buffers de instancias.

La GPU hace todo el trabajo pesado.

## Primeros resultados

Ya están integrados los primeros efectos:

- Chispas generadas desde la barra vertical del coche de choque.
- Emisiones esporádicas desde la parte inferior del vehículo.

Son efectos simples, pero importantes:

- Validan el pipeline.
- Permiten medir rendimiento.
- Sirven como base para efectos más complejos.

![ParicleCarr]({{ "/assets/images/imagesPosts/SparkPArticles.png" | relative_url }})

## Siguiente paso

Una vez validado el sistema, las partículas dejan de ser “efecto visual” y pasan a ser herramienta:

- Impactos.
- Fragmentación.
- Posible integración con voxels.

Y a por el siguiente tema....