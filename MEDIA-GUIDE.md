# Guía de Media para Posts

## Imágenes

### Imagen simple
```markdown
![Descripción](/assets/images/nombre.png)
```

### Imagen con caption
```html
<figure>
  <img src="/assets/images/screenshot.png" alt="Screenshot del juego">
  <figcaption>Primera versión del sistema de colisiones</figcaption>
</figure>
```

### Galería de imágenes
```html
<div class="gallery">
  <img src="/assets/images/img1.png" alt="Imagen 1">
  <img src="/assets/images/img2.png" alt="Imagen 2">
  <img src="/assets/images/img3.png" alt="Imagen 3">
</div>
```

### Comparación antes/después
```html
<div class="comparison">
  <figure>
    <img src="/assets/images/antes.png" alt="Antes">
    <figcaption class="before">Original 1990</figcaption>
  </figure>
  <figure>
    <img src="/assets/images/despues.png" alt="Después">
    <figcaption class="after">Remake 2025</figcaption>
  </figure>
</div>
```

### GIF animado con etiqueta
```html
<div class="gif-container">
  <img src="/assets/images/demo.gif" alt="Demo de gameplay">
</div>
```

---

## Vídeos

### YouTube (recomendado para vídeos largos)
```html
<div class="video-container">
  <iframe src="https://www.youtube.com/embed/VIDEO_ID" allowfullscreen></iframe>
</div>
```

### Vimeo
```html
<div class="video-container">
  <iframe src="https://player.vimeo.com/video/VIDEO_ID" allowfullscreen></iframe>
</div>
```

### Vídeo local (MP4)
```html
<div class="video-container">
  <video controls>
    <source src="/assets/videos/demo.mp4" type="video/mp4">
  </video>
</div>
```

### Vídeo local sin contenedor (más simple)
```html
<video controls width="100%">
  <source src="/assets/videos/clip.mp4" type="video/mp4">
</video>
```

---

## Recomendaciones

### Formatos de imagen
- **PNG**: Screenshots, pixel art, imágenes con transparencia
- **JPG**: Fotos, imágenes con muchos colores
- **GIF**: Animaciones cortas (< 10 segundos)
- **WebP**: Alternativa más ligera (con fallback a PNG/JPG)

### Tamaños recomendados
- Ancho máximo: 900px (el contenedor del blog)
- Thumbnails/galería: 400-600px
- GIFs: Mantenerlos pequeños (< 5MB)

### Vídeos
- Clips cortos (< 30s): GIF o vídeo local
- Vídeos largos: YouTube/Vimeo (no consume espacio del repo)
- GitHub tiene límite de 1GB por repositorio

---

## Estructura de carpetas

```
assets/
├── images/
│   ├── posts/           # Imágenes de posts (por fecha o nombre)
│   │   ├── 2026-02/
│   │   └── 2026-03/
│   ├── arqueologia/     # Material del Autocrash original
│   └── general/         # Logos, iconos, etc.
└── videos/
    └── clips/           # Clips cortos locales
```
