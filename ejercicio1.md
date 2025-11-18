# EJERCICIO 1 — Descripción paso a paso para desplegar el tema Jekyll “minima” en GitHub Pages

Fecha: 13 de noviembre de 2025

## Introducción

En este documento se describen, en detalle y en formato paso a paso, los procesos para:

- Crear, configurar y probar un sitio Jekyll usando el tema oficial `minima`.
- Personalizar páginas y posts (añadir al menos 1 página nueva y 3 publicaciones).
- Desplegar el sitio en GitHub Pages .


## 1) Crear un nuevo sitio Jekyll con tema `minima`

1. Crear el sitio (desde el directorio donde quieras trabajar):

```bash
jekyll new miblog2 
cd miblog2
```
  El tema minima ya esta instalado por defecto en jekyll asique no hace falta cambiar nada.


## 2) Configurar `_config.yml`

El archivo `_config.yml` contiene los pares clave/valor que Jekyll usa. A continuación un ejemplo con campos mínimos y cómo personalizarlo con tu nombre.

```yaml
title: "Mi blog - Tema Minima"
email: "tu_email@example.com"
description: "Un blog sobre [temática con sentido] — por Tu Nombre Apellidos"
baseurl: "/mi-blog" # <- para GitHub Pages de proyecto; usar "" si es un site de usuario (username.github.io)
url: "https://tu_cuenta_github.github.io" # Sin baseurl
author:
  name: "Tu Nombre Apellidos"
  email: "tu_email@example.com"
theme: minima
paginate: 5


```


## 3) Personalizar páginas (index.markdown, about.markdown) y crear una página nueva

Para personalizar entramos a los ficheros y los editamos con markdown para que despues se traduzca a html.

>Index.markdown:


>About.markdown:


## 4) Crear al menos 3 posts

Los posts deben ir en `_posts/` y el nombre de archivo debe tener formato `YYYY-MM-DD-titulo.markdown`.

Ejemplo de 3 posts mínimos:

`_posts/2025-11-13-presentacion-blog.markdown`:

En mi caso he creado bastantes post.


Consejos sobre imágenes:

- Añade las imágenes en `assets/imagenes/` (o donde prefieras). GitHub Pages sirve esos archivos estáticos.
- Usa rutas completas con `{{ site.baseurl }}` si `baseurl` no está vacío.

## 5) Git: inicializar, comitear y subir al repositorio de GitHub

1. Inicializar git (si no está):
```bash
git add .
git commit -m "Sitio Jekyll con tema minima - inicial"
git push origin gh-pages (este se hace para subirlo en la rama gh-pages)
```


2. Crear repositorio en GitHub (puedes usar la interfaz web o `gh` CLI). Supondremos que el repo se llama `mi-blog`.

```bash
git remote add origin https://github.com/tu_cuenta_github/mi-blog.git
git branch -M main
git push -u origin main
```

3. En GitHub: ve a Settings → Pages. Selecciona la rama `main` (o `gh-pages` si prefieres publicar contenido estático) y la carpeta `/ (root)` como fuente. Guarda.

Notas sobre ramas y estrategias de despliegue:

- Estrategia A (recomendada, simple): Subir el código fuente Jekyll a `main`. GitHub Pages construye el sitio automáticamente usando su motor Jekyll (si el tema y las gemas son compatibles con GitHub Pages). Configura Pages en `main` y site estará disponible en `https://tu_cuenta_github.github.io/mi-blog/` si `baseurl` está correctamente puesto a `/mi-blog`.
- Estrategia B (compilar localmente): Ejecutar `bundle exec jekyll build` y subir la carpeta `_site` a la rama `gh-pages`. En GitHub Pages configuras la rama `gh-pages` y la carpeta `/ (root)` para servir contenido estático. Esta estrategia evita depender del builder de GitHub y te permite usar plugins no soportados por Pages.

## 6) Ajustes finos y ejemplos prácticos para `baseurl` y rutas

- Si `baseurl` = "/mi-blog" entonces en las plantillas y enlaces escribe: `{{ site.baseurl }}{{ post.url }}` o para assets: `{{ site.baseurl }}/assets/imagenes/ejemplo.jpg`.
- Si `baseurl` = "" (sitio de usuario), no uses `{{ site.baseurl }}`.

## 7) Verificación local y checks rápidos

1. Probar localmente antes de subir:cd 

```bash
bundle exec jekyll serve
# Visitar http://localhost:4000/mi-blog/ (si usas baseurl)
```

2. Comprueba que en la cabecera o pie aparece: **Tu Nombre Apellidos** — verifica `_config.yml` y los `author` de los posts.

3. Comprobar enlaces rotos y rutas de imágenes.


## 8) URLs solicitadas (coloca tus enlaces reales aquí)

- URL del sitio Jekyll con Lagrange en GitHub Pages (ejercicio 2) (ejemplo):

  https://tu_cuenta_github.github.io/lagrange/

- URL del repositorio del TEMA ELEGIDO (ejercicio 3) (ejemplo):

  https://github.com/tu_cuenta_github/otro_tema/

- URL del sitio con TEMA ELEGIDO en Netlify (ejercicio 3) (ejemplo):

  https://nombre_sitio.netlify.app

- URL del repositorio de la actividad2-1 (sitio en MkDocs) (ejemplo):

  https://github.com/tu_cuenta_github/actividad2_1/

- URL del sitio MkDocs desplegado en GitHub Pages (ejemplo):

  https://tu_cuenta_github.github.io/actividad2_1/

- URL del sitio MkDocs desplegado en Cloudflare Pages (ejemplo):

  https://nombre_sitio2.pages.dev

