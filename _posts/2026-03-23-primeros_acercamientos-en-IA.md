---
layout: post
title: "Introducimos IA"
subtitle: "Primeros acercamientos"
date: 2026-03-23
tags: [meta, IA]
---

Empiezo a explorar la posibilidad de introducir IA basada en redes neuroevolutivas.

No como sistema accesorio, sino como parte central del comportamiento del juego.

Cada agente en Autocrash puede existir en dos estados completamente distintos:

- Conductor (dentro de un coche).
- Peatón (fuera del coche).

Aparece una decisión de diseño:

¿Una única red neuronal o dos redes separadas?

## Separación de contextos

La opción más lógica es utilizar dos redes independientes por agente.

Un cerebro conductor.  
Un cerebro peatón.

Las razones son claras.

Las entradas (inputs) son radicalmente distintas:

**Conductor:**
- Raycasts.
- Detección de coches cercanos.
- Evaluación del tipo de impacto (frontal/lateral).

**Peatón:**
- Posición de coches en movimiento.
- Distancia a coches vacíos.
- Entorno inmediato de riesgo.

Las salidas (outputs) también difieren:

**Conductor:**
- Giro / dirección de conducción.

**Peatón:**
- Movimiento en dos ejes.

Intentar unificar ambos comportamientos en una sola red introduce ruido innecesario y dificulta la convergencia.

Por lo tanto, creo que separar simplifica el problema.

## Funciones de fitness

Cada cerebro tiene su propio criterio de éxito:

**Conductor:**
- Maximizar velocidad. (Para acentuar el efecto del impacto)
- Impactar lateralmente a otros coches.
- Evitar ser golpeado lateralmente.

**Peatón:**
- Alcanzar un coche vacío.
- Minimizar el tiempo expuesto.
- Evitar ser atropellado.

El comportamiento óptimo en ambos casos no solo es distinto, sino casi opuesto.

## Coevolución

Lo interesante aparece al evolucionar ambos sistemas de forma conjunta.

Los conductores mejoran en impacto.  
Eso genera más peatones.

Los peatones mejoran en evasión.  
Eso obliga a los conductores a adaptarse.

Se genera una dinámica coevolutiva:

Una carrera armamentística entre comportamientos.

El sistema no está diseñado explícitamente para ser complejo.  
La complejidad emerge sola.

## Genoma del agente

El genoma completo de un agente está formado por:

- Pesos de la red de conducción.
- Pesos de la red de peatón.

La selección se realiza sobre el agente completo.

No gana el mejor conductor.  
No gana el mejor peatón.

Gana el agente equilibrado.

El que conduce bien y sobrevive cuando no lo hace.

## Implicaciones

Este enfoque permite:

- Comportamientos emergentes no diseñados explícitamente.
- Adaptación dinámica a estrategias dominantes.
- Evolución continua del sistema sin scripting manual.

Autocrash deja de ser solo un juego.

Empieza a comportarse como un ecosistema.