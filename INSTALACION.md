# Guía Completa de Instalación y Configuración

## Autocrash Devlog - De cero a online

Esta guía cubre todo el proceso: crear el repositorio, configurar GitHub Pages, activar comentarios y publicar tu primer post.

---

## Índice

1. [Requisitos previos](#1-requisitos-previos)
2. [Crear el repositorio en GitHub](#2-crear-el-repositorio-en-github)
3. [Subir los archivos](#3-subir-los-archivos)
4. [Activar GitHub Pages](#4-activar-github-pages)
5. [Configurar el dominio (opcional)](#5-configurar-dominio-personalizado-opcional)
6. [Activar comentarios con Giscus](#6-activar-comentarios-con-giscus)
7. [Personalizar la configuración](#7-personalizar-la-configuración)
8. [Escribir y publicar posts](#8-escribir-y-publicar-posts)
9. [Añadir imágenes y vídeos](#9-añadir-imágenes-y-vídeos)
10. [Flujo de trabajo diario](#10-flujo-de-trabajo-diario)
11. [Solución de problemas](#11-solución-de-problemas)

---

## 1. Requisitos previos

### Necesitas:

- **Cuenta de GitHub** → [github.com](https://github.com) (gratuita)
- **Git instalado** en tu ordenador
  - Windows: [git-scm.com](https://git-scm.com/download/win)
  - Mac: `xcode-select --install` en Terminal
  - Linux: `sudo apt install git`

### Verificar que Git está instalado:

```bash
git --version
```

Debería mostrar algo como `git version 2.x.x`

### Configurar Git (solo la primera vez):

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

---

## 2. Crear el repositorio en GitHub

### Paso a paso:

1. Entra en [github.com](https://github.com) y haz login
2. Clic en el botón **+** (arriba a la derecha) → **New repository**
3. Rellena:
   - **Repository name**: `autocrash-devlog`
   - **Description**: `Devlog del remake de Autocrash (ZX Spectrum 1990)`
   - **Public** ✓ (necesario para GitHub Pages gratuito)
   - **NO** marques "Add a README file"
   - **NO** marques "Add .gitignore"
4. Clic en **Create repository**

GitHub te mostrará una página con instrucciones. Déjala abierta.

---

## 3. Subir los archivos

### Opción A: Desde línea de comandos (recomendado)

1. Descomprime el archivo `autocrash-devlog.zip` en tu ordenador
2. Abre una terminal y navega a la carpeta:

```bash
cd ruta/donde/descomprimiste/autocrash-devlog
```

3. Inicializa Git y sube:

```bash
# Inicializar repositorio local
git init

# Añadir todos los archivos
git add .

# Crear el primer commit
git commit -m "Versión inicial del devlog"

# Conectar con GitHub (sustituye TU_USUARIO)
git remote add origin https://github.com/TU_USUARIO/autocrash-devlog.git

# Subir a GitHub
git branch -M main
git push -u origin main
```

Te pedirá autenticación. Usa tu usuario de GitHub y un **Personal Access Token** como contraseña (ver sección de problemas si no lo tienes).

### Opción B: Subir archivos desde la web de GitHub

1. En la página del repositorio vacío, clic en **uploading an existing file**
2. Arrastra todos los archivos de la carpeta descomprimida
3. Escribe un mensaje de commit: "Versión inicial"
4. Clic en **Commit changes**

⚠️ Esta opción puede dar problemas con carpetas vacías. La opción A es más fiable.

---

## 4. Activar GitHub Pages

### Paso a paso:

1. En tu repositorio, ve a **Settings** (pestaña superior)
2. En el menú lateral, clic en **Pages**
3. En **Source**, selecciona:
   - **Deploy from a branch**
4. En **Branch**, selecciona:
   - Branch: `main`
   - Folder: `/ (root)`
5. Clic en **Save**

### Esperar el despliegue:

- GitHub tarda 1-3 minutos en construir el sitio
- Refresca la página de Settings → Pages
- Verás un mensaje: **"Your site is live at https://TU_USUARIO.github.io/autocrash-devlog/"**

### Verificar:

Visita la URL. Deberías ver tu blog funcionando.

---

## 5. Configurar dominio personalizado (opcional)

Si quieres usar un dominio propio como `autocrash.dev`:

### En tu proveedor de dominio:

Añade un registro CNAME:
```
Tipo: CNAME
Nombre: www (o @ para el dominio raíz)
Valor: TU_USUARIO.github.io
```

### En GitHub:

1. Settings → Pages → Custom domain
2. Escribe tu dominio: `www.tudominio.com`
3. Clic en **Save**
4. Marca **Enforce HTTPS** (puede tardar unas horas en activarse)

### En `_config.yml`:

```yaml
url: "https://www.tudominio.com"
baseurl: ""  # Dejar vacío con dominio propio
```

---

## 6. Activar comentarios con Giscus

Giscus usa GitHub Discussions para los comentarios. Es gratuito y sin publicidad.

### 6.1 Activar Discussions en el repositorio

1. Ve a tu repositorio → **Settings**
2. Baja hasta **Features**
3. Marca ✓ **Discussions**
4. Clic en **Set up discussions** si aparece

### 6.2 Configurar Giscus

1. Ve a [giscus.app](https://giscus.app)
2. Rellena el formulario:

   **Repository:** `TU_USUARIO/autocrash-devlog`
   
   **Page ↔ Discussions Mapping:** `pathname` (recomendado)
   
   **Discussion Category:** Selecciona o crea "Comentarios" / "Comments"
   
   **Features:**
   - ✓ Enable reactions
   - Theme: `dark` (para que combine con el blog)

3. Giscus generará un código. Busca estos valores:
   ```
   data-repo="TU_USUARIO/autocrash-devlog"
   data-repo-id="R_xxxxxxxxxx"
   data-category="Comentarios"
   data-category-id="DIC_xxxxxxxxxx"
   ```

### 6.3 Actualizar _config.yml

Abre `_config.yml` y actualiza la sección giscus:

```yaml
giscus:
  enabled: true
  repo: "TU_USUARIO/autocrash-devlog"
  repo_id: "R_xxxxxxxxxx"        # ← Copia de giscus.app
  category: "Comentarios"
  category_id: "DIC_xxxxxxxxxx"  # ← Copia de giscus.app
  mapping: "pathname"
  reactions_enabled: "1"
  theme: "dark"
```

### 6.4 Subir los cambios

```bash
git add _config.yml
git commit -m "Configurar Giscus para comentarios"
git push
```

Espera 1-2 minutos y los comentarios estarán activos.

---

## 7. Personalizar la configuración

### Archivo `_config.yml`

```yaml
# Información básica
title: "Autocrash Devlog"
description: "El remake de un juego de ZX Spectrum de 1990"
author: "Luis Angel Alda"

# URLs - IMPORTANTE ajustar estos
url: "https://TU_USUARIO.github.io"  # Tu URL de GitHub Pages
baseurl: "/autocrash-devlog"          # Nombre del repositorio

# Redes sociales (opcional)
social:
  github: TU_USUARIO
  twitter: TU_TWITTER  # Si tienes
```

### Cambiar colores del tema

Edita `assets/css/main.css`, sección `:root`:

```css
:root {
  /* Colores principales - ajusta a tu gusto */
  --accent: var(--spectrum-cyan-bright);     /* Color principal */
  --accent-alt: var(--spectrum-magenta-bright); /* Color secundario */
  
  /* Fondo */
  --bg-primary: #0a0a0f;    /* Fondo principal */
  --bg-card: #1a1a24;       /* Fondo de tarjetas */
}
```

---

## 8. Escribir y publicar posts

### Crear un nuevo post

1. Crea un archivo en `_posts/` con el formato:
   ```
   YYYY-MM-DD-titulo-del-post.md
   ```
   
   Ejemplo: `2026-02-15-sistema-de-colisiones.md`

2. Añade el encabezado (front matter):

```markdown
---
layout: post
title: "Sistema de colisiones"
subtitle: "Cómo detectar impactos entre voxels"
date: 2026-02-15
tags: [engine, física, técnico]
---

Aquí empieza el contenido del post...
```

3. Escribe el contenido en Markdown

### Sintaxis Markdown básica

```markdown
## Encabezado grande
### Encabezado mediano

Párrafo normal con **negrita** y *cursiva*.

- Lista con viñetas
- Otro elemento

1. Lista numerada
2. Segundo elemento

[Texto del enlace](https://url.com)

![Descripción imagen](/assets/images/foto.png)

`código en línea`

​```python
# Bloque de código
def hola():
    print("Hola")
​```

> Esto es una cita
```

### Publicar el post

```bash
git add _posts/2026-02-15-sistema-de-colisiones.md
git commit -m "Nuevo post: Sistema de colisiones"
git push
```

El post aparecerá en 1-2 minutos.

---

## 9. Añadir imágenes y vídeos

### Imágenes

1. Guarda la imagen en `assets/images/posts/`
2. En el post:

```markdown
![Descripción](/assets/images/posts/mi-imagen.png)
```

### Imagen con caption

```html
<figure>
  <img src="/assets/images/posts/screenshot.png" alt="Screenshot">
  <figcaption>Primera versión del motor de colisiones</figcaption>
</figure>
```

### Galería

```html
<div class="gallery">
  <img src="/assets/images/posts/img1.png" alt="Imagen 1">
  <img src="/assets/images/posts/img2.png" alt="Imagen 2">
  <img src="/assets/images/posts/img3.png" alt="Imagen 3">
</div>
```

### Comparación antes/después

```html
<div class="comparison">
  <figure>
    <img src="/assets/images/arqueologia/spectrum-1990.png" alt="Original">
    <figcaption class="before">ZX Spectrum 1990</figcaption>
  </figure>
  <figure>
    <img src="/assets/images/posts/remake-2025.png" alt="Remake">
    <figcaption class="after">Remake 2025</figcaption>
  </figure>
</div>
```

### GIF animado

```html
<div class="gif-container">
  <img src="/assets/images/posts/demo.gif" alt="Demo de gameplay">
</div>
```

### Vídeo de YouTube

```html
<div class="video-container">
  <iframe src="https://www.youtube.com/embed/ID_DEL_VIDEO" allowfullscreen></iframe>
</div>
```

Para obtener el ID: en la URL `youtube.com/watch?v=XXXXX`, el ID es `XXXXX`

### Vídeo local

```html
<div class="video-container">
  <video controls>
    <source src="/assets/videos/demo.mp4" type="video/mp4">
  </video>
</div>
```

⚠️ Recuerda: GitHub tiene límite de 1GB. Para vídeos largos, usa YouTube.

---

## 10. Flujo de trabajo diario

### Escribir un post nuevo

```bash
# 1. Crear el archivo del post
# _posts/2026-02-20-nuevo-post.md

# 2. Añadir imágenes si las hay
# assets/images/posts/

# 3. Subir todo
git add .
git commit -m "Nuevo post: Título del post"
git push
```

### Editar un post existente

```bash
# 1. Editar el archivo
# 2. Subir cambios
git add _posts/archivo-editado.md
git commit -m "Corregir typo en post X"
git push
```

### Ver cambios antes de subir

```bash
git status          # Ver qué archivos han cambiado
git diff            # Ver los cambios en detalle
```

### Descargar cambios (si editas desde otro ordenador)

```bash
git pull
```

---

## 11. Solución de problemas

### "Authentication failed" al hacer push

GitHub ya no acepta contraseñas. Necesitas un Personal Access Token:

1. GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Generate new token (classic)
3. Nombre: "Git local"
4. Expiration: 90 días o "No expiration"
5. Scopes: marca `repo` (todo el grupo)
6. Generate token
7. **Copia el token** (solo se muestra una vez)
8. Usa el token como contraseña cuando Git lo pida

### El sitio no se actualiza

1. Ve a tu repositorio → Actions
2. Verifica que el workflow "pages-build-deployment" está corriendo
3. Si hay error (❌), haz clic para ver los detalles
4. Errores comunes:
   - Sintaxis incorrecta en `_config.yml`
   - Front matter mal formado en un post

### Los comentarios no aparecen

1. Verifica que Discussions está activado en el repo
2. Comprueba que los IDs en `_config.yml` coinciden con giscus.app
3. Prueba en una ventana de incógnito (puede ser caché)

### Las imágenes no cargan

1. Verifica la ruta: debe empezar con `/assets/images/...`
2. Comprueba mayúsculas/minúsculas (Linux es sensible)
3. Asegúrate de que la imagen está subida (`git add`, `git push`)

### Error "baseurl" - enlaces rotos

Si usas GitHub Pages con repositorio (no dominio propio):
```yaml
baseurl: "/autocrash-devlog"  # Debe coincidir con nombre del repo
```

Si usas dominio propio:
```yaml
baseurl: ""  # Vacío
```

### Probar localmente (opcional)

Si quieres ver los cambios antes de subir:

```bash
# Instalar Ruby y Jekyll (una vez)
# Windows: https://rubyinstaller.org
# Mac: viene instalado
# Linux: sudo apt install ruby-full

# Instalar dependencias
bundle install

# Ejecutar servidor local
bundle exec jekyll serve

# Abrir http://localhost:4000/autocrash-devlog/
```

---

## Resumen de comandos Git

| Acción | Comando |
|--------|---------|
| Ver estado | `git status` |
| Añadir archivos | `git add .` |
| Crear commit | `git commit -m "mensaje"` |
| Subir a GitHub | `git push` |
| Descargar cambios | `git pull` |
| Ver historial | `git log --oneline` |

---

## Checklist final

- [ ] Repositorio creado en GitHub
- [ ] Archivos subidos
- [ ] GitHub Pages activado
- [ ] Sitio funcionando en `https://TU_USUARIO.github.io/autocrash-devlog/`
- [ ] Discussions activado
- [ ] Giscus configurado en `_config.yml`
- [ ] Comentarios funcionando
- [ ] Primer post publicado

---

¡Listo! El blog está operativo. A documentar el desarrollo de Autocrash.
