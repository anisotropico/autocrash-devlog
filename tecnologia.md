---
layout: page
title: Tecnología
subtitle: El Autocrash Engine
permalink: /tecnologia/
---

## Arquitectura del motor

Autocrash se construye sobre un motor propio diseñado específicamente para simulación física de voxels con soporte multijugador determinista.

### Principios de diseño

- **Herramientas antes que contenido**: Construir el pipeline completo antes de crear assets
- **Determinismo absoluto**: Misma entrada = misma salida, siempre
- **Aritmética de punto fijo**: Sin flotantes, sin sorpresas entre plataformas
- **Destrucción a nivel de voxel**: Cada impacto modifica la geometría

### Componentes principales

#### Sistema de voxelización
Conversión de modelos a representación volumétrica con LOD dinámico y optimización de memoria.

#### Física determinista
Motor de colisiones y respuesta física que garantiza sincronización perfecta entre clientes.

#### Pipeline de renderizado
Renderizado de voxels con soporte para destrucción en tiempo real.

---

*Documentación técnica detallada en desarrollo. Se irá expandiendo durante el proyecto.*
