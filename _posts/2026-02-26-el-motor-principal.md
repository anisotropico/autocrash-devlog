---
layout: post
title: "El motor 3D"
subtitle: "Base sólida y próxima evolución"
date: 2026-02-26
tags: [meta, la base]
---

Autocrash no empieza desde cero.

Dispongo de un motor 3D propio que he utilizado en distintos proyectos anteriores, incluyendo desarrollos para PS4. Es un sistema pensado para exprimir rendimiento y ofrecer control total sobre el comportamiento del juego.
 
Es una base madura de la que podemos partir y añadir el conjunto e la parte voxel.

## Arquitectura actual

El motor incluye:

- Sistema de objetos, grupos y dummies combinables para generar variaciones estructurales.
- Gestión de lógica aplicada a escenas, objetos, grupos, dummies, etc.
- Módulo de texto 3D integrado.
- Sistema de sonido.
- Soporte multiidioma.
- Sistema de partículas controladas mediante shaders computacionales.
- Sistema de materiales con biblioteca predefinida y posibilidad de crear materiales personalizados.

La filosofía siempre ha sido clara:  
control explícito, rendimiento alto, mínima sobrecarga innecesaria.

Cada módulo existe porque cumple una función concreta dentro del juego. No hay capas decorativas.

En las siguientes imágenes, podemos apreciar objetos y sistemas de partículas que contempla el motor:

![ObjetosMixer]({{ "/assets/images/imagesPosts/ObjetosMixer.png" | relative_url }})

![ParticulasMixer]({{ "/assets/images/imagesPosts/ParticulasMixer.png" | relative_url }})

## Optimización como principio

El motor está diseñado para aprovechar completamente el hardware disponible.

La lógica y el render están claramente diferenciados.   
Los sistemas críticos están pensados para minimizar dependencias.

Es una arquitectura pensada para producir juegos sin que sobre ni falte nada.

## El siguiente paso

Sin embargo, hace tiempo que no realizo cambios profundos en él.

Y este proyecto es el momento perfecto para revisarlo.

No se trata de reescribirlo todo.  
Se trata de evolucionarlo.

Revisar módulos existentes.
Añadir el módulo Voxel.
Simplificar donde sea posible.  
Modernizar partes concretas.  
Adaptarlo mejor al enfoque voxel del nuevo Autocrash.

El objetivo no es añadir complejidad.

Autocrash será el banco de pruebas para llevar este motor al siguiente nivel.
