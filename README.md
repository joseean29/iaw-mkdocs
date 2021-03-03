# Creación de un sitio web estático con MkDocs y GithubPages

## Preparando la máquina

Esto lo podemos hacer en cualquier máquina, debemos tener instaladas las herramientas de github docker y docker-compose.

## Preparando nuestro repositorio y la estructura del directorio

En github, tenemos que crearnos un repositorio con el nombre que queramos. En nuestra máquina debemos crearnos la siguiente estructura de directorios:

```
└── proyecto
    ├── docs
    │   ├── about.md
    │   └── home.md
    └── mkdocs.yml
```

**En la carpeta docs irán las páginas que queremos publicar.**

El archivo mkdocs.yml deberá tener de base el siguiente contenido:

```
site_name: Blog de Jose Antonio
site_description: 'Sitio Mkdocs de Jose Antonio Abad Jurado en el que están sus prácticas de IAW'
site_author: Jose Antonio

nav:
    - Principal: index.md
    - Práctica 1: about.md
    - Práctica 2: practica2.md

theme:
  name: 'material'
  lenguage: 'es'
  palette:
    primary: 'blue grey'
    accent: 'black'
  front:
    text: 'Robot'
    code: 'Roboto Mono'
```

- site name. Indica el nombre de nuestro sitio web.

- **nav:** Esta sección crea el menú en el que se visualizarán nuestros posts, este archivo debe estar en la carpeta docs.

- **theme.** Es el tema que vamos a utilizar para nuestra página, podemos desarrollarlo con más opciones que podemos encontrar en la [documentación](https://www.mkdocs.org/#mkdocs) oficial. Arriba se puede ver como lo tengo confeccionado yo.

## Probando nuestro sitio de forma local

Con toda la estructura creada podemos lanzar un contenedor servidor que nos permita ver en tiempo real los cambios que hagamos. Este servidor nos sirve de forma local, aún no podremos lanzar la página a Github.

Lanzamos el contenedor local:

> docker run --rm -it -p 8000:8000 -v "$PWD":/docs squidfunk/mkdocs-material

Si ingresamos a localhost:8000 podremos ver nuestro sitio y empezar a añadirle contenido.

## Generar la documentación
También es posible generar directamente el sitio web sin tener que iniciar un servidor local de desarrollo. Para generar el sitio web automáticamente podemos ejecutar el siguiente comando:
```
docker run --rm -it -v "$PWD":/docs squidfunk/mkdocs-material build
```
El comando anterior creará un directorio llamado `site` donde guarda el sitio web que se ha generado. Luego habrá que renombrar este directorio a docs para que el blog se pueda visualizar directamente en html.

## Publicar la documentación en GitHub Pages

Es posible publicar la el sitio web en GitHub Pages con el siguiente comando:
´´´
docker run --rm -it -v ~/.ssh:/root/.ssh -v "$PWD":/docs squidfunk/mkdocs-material gh-deploy
´´´

# MI BLOG MKDOCS
**[joseean29.github.io/iaw-mkdocs](https://joseean29.github.io/iaw-mkdocs)**
