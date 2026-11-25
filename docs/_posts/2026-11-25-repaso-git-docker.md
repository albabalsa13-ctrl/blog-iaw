---
title: "Repaso de Comandos Git y Docker"
date: 2026-11-25
---

## 1. Comandos de Git

### Configuración e Inicialización
* **`git init`**: Inicializa un repositorio local de Git en el directorio actual.
* **`git config --global user.name "TuNombre"`**: Configura tu nombre de usuario de forma global para la firma de los commits.
* **`git config --global user.email "tu@email.com"`**: Establece tu dirección de correo electrónico global asociada a los commits.
* **`git config user.name` / `git config user.email`**: Consulta el nombre o correo configurado localmente.
* **`git config --global --add safe.directory 'ruta'`**: Añade una excepción a la lista de directorios seguros de Git para evitar errores de propiedad (*dubious ownership*) en Git Bash sobre Windows.

### Gestión de Estado y Área de Preparación
* **`git status`**: Muestra el estado del directorio de trabajo y del área de preparación.
* **`git add <archivo>`**: Añade un archivo específico al área de preparación.
* **`git add .`**: Añade todos los archivos y cambios del directorio actual al área de preparación.
* **`git add archivo1 archivo2`**: Permite añadir múltiples archivos específicos simultáneamente.
* **`git rm --cached <archivo>`**: Quita un archivo del área de preparación sin eliminarlo físicamente del equipo.
* **`git rm --cached . -r`**: Elimina del área de preparación de manera recursiva (entra en carpetas y subcarpetas) todos los archivos indicados.
* **`git diff`**: Muestra la diferencia de contenido línea por línea entre el área de trabajo y el último commit o estado staged.

### Guardado e Historial (*Commits*)
* **`git commit -m "Mensaje explicativo"`**: Guarda una captura del estado actual de los archivos situados en el área de preparación con un mensaje descriptivo.
* **`git log`**: Consulta el historial de commits realizados (muestra identificador SHA-1, autor, fecha y mensaje).

### Trabajo con Ramas (*Branches*) y Fusiones (*Merges*)
* **`git branch`**: Muestra el listado de ramas locales e indica mediante un asterisco (`*`) en cuál estás ubicado.
* **`git branch -M main`**: Renombra la rama actual a `main`.
* **`git switch -c <nombre-rama>`** (o **`git checkout -b <nombre-rama>`**): Crea una nueva rama local y se desplaza automáticamente a ella.
* **`git switch <nombre-rama>`** (o **`git checkout <nombre-rama>`**): Cambia a una rama ya existente.
* **`git merge <nombre-rama>`**: Integra las modificaciones de la rama indicada en la rama actual. Si surgen conflictos, permite resolverlos eligiendo qué cambios conservar antes de guardar y confirmar con commit.

### Repositorios Remotos y GitHub
* **`git clone <url-del-repositorio>`**: Descarga un repositorio remoto completo en una nueva carpeta local, configurando la rama principal y el remoto `origin`.
* **`git remote add origin <url>`**: Asocia un repositorio local a un repositorio remoto alojado en GitHub con la etiqueta `origin`.
* **`git remote -v`**: Lista la dirección URL configurada para descargar (*fetch*) y subir (*push*) cambios.
* **`git push -u origin <rama>`**: Sube la rama local por primera vez al remoto y vincula su seguimiento.
* **`git push`**: Sube al repositorio remoto los nuevos commits guardados localmente.
* **`git pull`**: Descarga los cambios del repositorio remoto y los fusiona en la rama local actual.

---

## Comandos de Docker y Docker Compose

### Gestión de imágenes y contenedores (Docker CLI)
* **`docker run <imagen>`**: Crea y ejecuta un contenedor a partir de una imagen. Si la imagen no está en local, la descarga automáticamente desde Docker Hub.
* **`docker ps`**: Lista los contenedores que están actualmente en ejecución.
* **`docker ps -a`**: Muestra todos los contenedores existentes, incluidos los que están detenidos.
* **`docker build`**: Construye una imagen de Docker a partir de un fichero `Dockerfile`.
* **`docker push`**: Sube una imagen local a un registro remoto como Docker Hub.
* **`docker rm <contenedor>`**: Elimina uno o varios contenedores detenidos.
* **`docker rmi <imagen>`**: Elimina una o varias imágenes descargadas en local.

### Orquestación con Docker Compose (`docker-compose.yml`)
* **`docker compose config --quiet`**: Valida la sintaxis y estructura del fichero `docker-compose.yml`. Si todo es correcto, termina sin mostrar ningún mensaje por pantalla.
* **`docker compose up`**: Crea, conecta y levanta todos los servicios definidos en el archivo `docker-compose.yml`.
* **`docker compose up -d`**: Levanta los servicios definidos en `docker-compose.yml` en segundo plano (modo *detached*), dejando la terminal libre.