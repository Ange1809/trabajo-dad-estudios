# Prácticas de Docker - Diseño y Arquitectura de Despliegue

Repositorio correspondiente a las actividades prácticas de la materia **Diseño y Arquitectura de Despliegue (DAD)**, enfocado en la configuración, despliegue y gestión de contenedores.

**Estudiante:** Angélica Morfa Morales  
**Repositorio base:** [docker-tutorial de joseluisgs](https://github.com/joseluisgs/docker-tutorial)

---

## Entorno de Desarrollo

La configuración utilizada para la resolución y prueba de los ejercicios es la siguiente:
* **Motor de contenedores:** Docker Desktop.
* **Subsistema Linux:** WSL 2 (Ubuntu) implementado en Windows.
* **Editor de código:** Visual Studio Code (utilizando la terminal integrada y acceso directo al shell de los contenedores).

---

## Resumen de Actividades

A continuación se detalla el progreso de los ejercicios propuestos:

* **[Ejemplo 1](./ejemplo-1/) (Completado):** Actualización de la imagen base en el `Dockerfile` para resolver conflictos de dependencias, despliegue del contenedor web y edición en tiempo real del código fuente utilizando Vim desde la consola interna.
* **Ejemplo 2 (Pendiente):** Ejecución y análisis funcional del script de automatización `run.sh`.
* **Ejemplo 3 (Pendiente):** (Actividad a definir).

---

## Estructura de Directorios

```text
📦 trabajo-dad-estudios
 ┣ 📜 README.md
 ┣ 📂 ejemplo-1
 ┃ ┣ 📜 README.md
 ┃ ┣ 📜 Dockerfile
 ┃ ┣ 📂 src
 ┃ ┗ 📂 screenshots
 ┃   ┣ 🖼️ 01-build.png
 ┃   ┣ 🖼️ 02-sitio-inicial.png
 ┃   ┣ 🖼️ 03-install-vim.png
 ┃   ┣ 🖼️ 04-vi-edit.png
 ┃   ┗ 🖼️ 05-resultado.png
 ┗ 📂 ejemplo-2


---

### 2. Archivo del primer ejercicio (Adentro de la carpeta `ejemplo-1/README.md`)

```
# Ejemplo 1: Edición de Contenedores en Ejecución

## Objetivo de la Práctica
Desplegar un servidor web mediante Docker, solucionar los conflictos de versión presentes en la imagen base y realizar modificaciones directas en el archivo `index.html` accediendo a la terminal del contenedor.

## Corrección del Dockerfile
Durante el despliegue inicial, se detectó que la imagen original (`php:7.0-apache`) presentaba errores de compatibilidad con librerías modernas (GLIBC) al intentar establecer conexión con el shell. 

Para solucionar este incidente, se modificó el `Dockerfile` apuntando a una versión reciente y estable de PHP:
```dockerfile
FROM php:8.2-apache
COPY src/ /var/www/html/
