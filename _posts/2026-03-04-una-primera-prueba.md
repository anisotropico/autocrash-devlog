---
layout: post
title: "Mi primera prueba real"
subtitle: "Programar en un MiniPC con N95"
date: 2026-03-04
tags: [meta, prueba1]
---

Empiezan a verse resultados.

Vamos con un detalle: todo el desarrollo se está realizando en un Mini PC con un Intel N95, sin gráfica dedicada.

Nada de GPU monstruosas.  
Nada de hardware sobredimensionado.

Y funciona.

El motor mueve la escena voxel con suavizado de aristas sin problemas. La arquitectura responde como estaba previsto.

![Prueba1]({{ "/assets/images/imagesPosts/Prueba1.png" | relative_url }})

## Decisiones necesarias

He tenido que desactivar el MSAA. (Aunque se puede volver a activar con un simple cambio)
Demasiado coste para una máquina tan contenida.

El objetivo aquí no es exhibir potencia bruta.  
Es demostrar eficiencia estructural.

## Ventaja de la arquitectura propia

Con motores comerciales generalistas sería muy difícil alcanzar este nivel de control fino sobre el rendimiento en un hardware tan modesto.

Cuando controlas cada módulo, cada capa y cada llamada de render, puedes ajustar exactamente lo que necesitas y eliminar lo superfluo.

No hay sistemas en segundo plano consumiendo recursos sin que lo sepas.  
No hay abstracciones pesadas que penalicen escenarios simples.

Hay sistema. Y punto.

## ¿Cambiaré de máquina?

Es posible que en algún momento necesite un equipo más potente. (Lo iremos viendo)

Pero no es el objetivo inmediato.

Esto es un reto técnico.

Trabajar en un entorno limitado obliga a pensar mejor.  
Obliga a medir.  
Obliga a entender dónde está realmente el coste.

Son formas de trabajar que se han ido perdiendo con la abundancia de recursos y las prisas. Y probablemente se perderán aún más con la automatización creciente y la llegada masiva de herramientas basadas en IA.

Pero optimizar no es nostalgia.  
Es comprensión profunda del sistema.

Incluso con hardware modesto se pueden hacer cosas muy interesantes.

La clave no es la potencia.  
Es el diseño.