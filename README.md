# Autocrash Devlog

Blog de desarrollo del remake de Autocrash (ZX Spectrum, 1990).

## Instalación local

```bash
# Instalar dependencias
bundle install

# Ejecutar servidor local
bundle exec jekyll serve

# Visitar http://localhost:4000/autocrash-devlog/
```

## Despliegue en GitHub Pages

### 1. Crear repositorio

Crea un repositorio en GitHub llamado `autocrash-devlog` (o el nombre que prefieras).

### 2. Subir el código

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/autocrash-devlog.git
git push -u origin main
```

### 3. Activar GitHub Pages

1. Ve a **Settings** → **Pages**
2. En "Source", selecciona **Deploy from a branch**
3. Selecciona la rama `main` y carpeta `/ (root)`
4. Guarda

Tu blog estará en: `https://TU_USUARIO.github.io/autocrash-devlog/`

### 4. Configurar comentarios con Giscus

1. Ve a [giscus.app](https://giscus.app/)
2. Activa **Discussions** en tu repositorio (Settings → Features → Discussions)
3. Rellena el formulario de giscus con tu repositorio
4. Copia los valores `data-repo-id` y `data-category-id`
5. Actualiza `_config.yml` con estos valores

## Estructura

```
autocrash-devlog/
├── _config.yml          # Configuración de Jekyll
├── _layouts/            # Plantillas HTML
│   ├── default.html     # Layout base
│   ├── post.html        # Layout para posts
│   └── page.html        # Layout para páginas
├── _posts/              # Posts del devlog (YYYY-MM-DD-titulo.md)
├── assets/
│   └── css/
│       └── main.css     # Estilos
├── arqueologia/         # Material del juego original
├── index.html           # Página de inicio
├── about.md             # Sobre el proyecto
└── tecnologia.md        # Documentación técnica
```

## Crear un nuevo post

Crea un archivo en `_posts/` con el formato `YYYY-MM-DD-titulo.md`:

```markdown
---
layout: post
title: "Título del post"
subtitle: "Subtítulo opcional"
date: 2026-02-15
tags: [tag1, tag2]
---

Contenido del post en Markdown...
```

## Personalización

### Cambiar colores

Edita las variables CSS en `assets/css/main.css`:

```css
:root {
  --accent: #00D7D7;      /* Color principal (cyan Spectrum) */
  --accent-alt: #D700D7;  /* Color secundario (magenta Spectrum) */
  /* ... */
}
```

### Desactivar efecto scanlines

Elimina o comenta `<div class="scanlines"></div>` en `_layouts/default.html`.

---

De ZX Spectrum a 2025. Cerrando el círculo.
