# EJERCICIO 3 — Importar y desplegar un tema Jekyll (tema elegido: `cayman`) en Netlify


## 1) Elección del tema

He elegido `jekyll-theme-cayman` por ser un tema ligero, gratuito y fácil de personalizar.
Información del tema elegido:

- Nombre: `jekyll-theme-cayman`
- Repositorio / información: https://github.com/pages-themes/cayman

---

## 2) Preparar el repositorio localmente (crear sitio Jekyll y usar el tema)


1. Bajamos el repositorio a local 

```bash
bit clone url + token
```

2. Modifica `_config.yml` para usar el tema y personalizar datos básicos. Ejemplo mínimo:

```yaml
title: "Asier - Tema Cayman"
email: "Arodriguezo02@gmail.com"
description: "Blog de ejemplo con Jekyll y Cayman"
url: "https://tu_usuario.github.io"
baseurl: "" # si es sitio de usuario; si es sitio de proyecto p. ej. "/mi-proyecto"
theme: jekyll-theme-cayman
author:
  name: "Asier Rodriguez"
```


5. Instala dependencias con Bundler:

```bash
bundle install
```

6. Ejecuta el servidor localmente para probar:

```bash
bundle exec jekyll serve --livereload
# Abrir: http://localhost:4000
```

Si todo funciona, verás el sitio con el tema Cayman.

---

## 3) Personalizar la página principal y crear páginas y posts

Ejemplos y recomendaciones para personalizar contenido. En los ejemplos usaré la temática: "Pequeña biblioteca local" (una temática distinta a los ejercicios 1 y 2).

### Ejemplo `index.md` (principal)

```markdown
---
layout: home
title: Inicio
---

Bienvenido a **Biblioteca Vecinal** — un espacio para compartir recursos, reseñas y noticias.

- **Horario:** Lunes a Viernes, 10:00–18:00
- **Dirección:** Calle Ficticia, 42

¡Explora los posts recientes abajo!

```

### Ejemplo `about.md`

```markdown
---
layout: page
title: Sobre la Biblioteca
permalink: /about/
---

La Biblioteca Vecinal es un proyecto comunitario. Mi nombre es **Tu Nombre Apellidos** y coordino actividades.

Contacto: tu_email@example.com

```

### Crear una página nueva: `eventos.md`

```markdown
---
layout: page
title: Eventos
permalink: /eventos/
---

Listado de eventos próximos:

1. Cuentacuentos — 2025-12-01
2. Intercambio de libros — 2026-01-15

```

### Crear 3 posts de ejemplo (en `_posts/`)

Nombres de archivo (ejemplos):

- `_posts/2025-11-25-reseña-novela-juvenil.md`
- `_posts/2025-11-26-resumen-evento-cuentacuentos.md`
- `_posts/2025-11-27-novedades-biblioteca.md`

Ejemplo de post:

```markdown
---
layout: post
title: "Reseña: 'El mapa de las estrellas'"
date: 2025-11-25 09:00:00 +0100
categories: [reseñas]
author: "Tu Nombre Apellidos"
---

Una reseña breve de la novela juvenil que recomendamos en la Biblioteca Vecinal.

![Portada del libro](/assets/imagenes/portada.jpg)

```

Consejos sobre imágenes y assets:

- Crea el directorio `assets/imagenes/` y añade las imágenes allí.
- Al referenciarlas en posts usa rutas relativas al site, p. ej. `/assets/imagenes/portada.jpg` o `{{ site.baseurl }}/assets/imagenes/portada.jpg` si usas `baseurl`.

---

## 4) Subir el proyecto a GitHub

1. Inicializa git y haz commit:

```bash
git init
git add .
git commit -m "Sitio con tema Cayman - inicial"
```

2. Crea el repositorio en GitHub (p. ej. `biblioteca-vecinal`) y sube:

```bash
git remote add origin https://github.com/tu_usuario/biblioteca-vecinal.git
git branch -M main
git push -u origin main
```

---

## 5) Desplegar en Netlify

Netlify construye tu sitio desde el repositorio y sirve los archivos estáticos. Pasos resumidos:

1. Crea una cuenta en Netlify (o inicia sesión) en https://app.netlify.com/
2. En Netlify, elige "Add new site" → "Import from Git" → conecta tu cuenta de GitHub y autoriza Netlify.
3. Selecciona el repositorio (`biblioteca-vecinal` en este ejemplo).
4. Configura los valores de build:

- Build command: `bundle exec jekyll build`
- Publish directory: `_site`

Opcionales y útiles:

- Environment variable `JEKYLL_ENV=production` (Netlify suele configurar variables, puedes añadirla).
- Si usas Bundler y dependencias, Netlify instalará `bundle` y ejecutará `bundle install` automáticamente antes del build si detecta `Gemfile`.

5. Pulsa Deploy site. Netlify iniciará la build y te dará una URL provisional del tipo `https://nombre-sitio.netlify.app`.

6. Cada vez que empujes a la rama configurada (ej. `main`), Netlify reconstruirá el sitio automáticamente.

Notas sobre build errors comunes:

- Si Netlify falla por falta de dependencias, revisa `Gemfile` y `Gemfile.lock` y que `bundle install` funcione localmente.
- Si el tema requiere plugins privados, podrías necesitar compilar localmente y subir `_site` a un repo separado, o ajustar `netlify.toml` y dependencias.

Ejemplo de `netlify.toml` (opcional):

```toml
[build]
  command = "bundle exec jekyll build"
  publish = "_site"

[context.production.environment]
  JEKYLL_ENV = "production"
```

---

## 6) Buenas prácticas y comprobaciones

- Verifica que en el footer o en la cabecera aparezca tu nombre tal y como quieres (`_config.yml` → `author.name`).
- Revisa rutas de imágenes y enlaces. Si usas `baseurl` añade `{{ site.baseurl }}` cuando sea necesario.
- Añade en `README.md` del repositorio instrucciones para ejecutar localmente (`bundle install`, `bundle exec jekyll serve`).

---

## 7) Ejemplo de tabla resumen

| Paso | Comando/Acción |
|---|---|
| Crear sitio | `jekyll new sitio-netlify --skip-bundle` |
| Instalar gems | `bundle install` |
| Probar local | `bundle exec jekyll serve` |
| Build Netlify | `bundle exec jekyll build` |
| Publicar Netlify | Publish dir: `_site` |

---

## 8) URLs solicitadas (rellena con tus enlaces reales)

- URL del repositorio del tema elegido (ejemplo):

  https://github.com/tu_usuario/biblioteca-vecinal

- URL del sitio desplegado en Netlify (ejemplo):

  https://nombre-sitio.netlify.app

Si además necesitas la URL en GitHub Pages (no aplicaría si sólo usas Netlify), sigue las indicaciones del Ejercicio 1 para Pages.

---

## 9) Siguientes pasos (ofrezco ayuda)

- Puedo crear en tu repo los archivos de ejemplo (`index.md`, `about.md`, `eventos.md`, y los 3 posts) y añadir un placeholder para la imagen en `assets/imagenes/`.
- Puedo ayudarte a configurar Netlify (paso a paso) una vez me confirmes el nombre del repositorio y si quieres que lo haga con la URL real.

Dime si quieres que cree los archivos de ejemplo ahora (y con qué temática exacta), o si prefieres que modifique `_config.yml` con tu nombre real.
