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
site_name: A PLACE FOR PACR

nav:
    - Principal: index.md
    - Acerca de: about.md
    - Pagina-prueba: prueba.md

theme: material
```

- **site name.** Especifica el nombre que tendrá nuestro sitio web.

- **nav:** Este apartado es importante, creará un pequeño menú en el que irán nuestras páginas, como se ve, a excepción de las dos primeras páginas (esas tienen que estar por defecto) primero ponemos un - seguido de el nombre que se mostrará para la página, a continuación se le pone : y se escribe el nombre que tiene el archivo Markdown que representa a la página, este archivo debe estar en la carpeta docs.

- **theme.** Es el tema que vamos a utilizar para nuestra página, podemos desarrollarlo con más opciones que podemos encontrar en la [documentación](https://www.mkdocs.org/#mkdocs) oficial.

## Probando nuestro sitio de forma local

Con toda la estructura creada podemos lanzar un contenedor servidor que nos permita ver en tiempo real los cambios que hagamos. Este servidor nos sirve de forma local, aún no podremos lanzar la página a Github.

Lanzamos el contenedor local:

> docker run --rm -it -p 8000:8000 -v "$PWD":/docs squidfunk/mkdocs-material

Si ingresamos a localhost:8000 podremos ver nuestro sitio y empezar a añadirle contenido.

# MI BLOG MKDOCS
**[joseean29.github.io/iaw-mkdocs]https://joseean29.github.io/iaw-mkdocs**
