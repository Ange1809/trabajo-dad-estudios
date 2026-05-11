# Estudios de Docker - DAD
**Alumna:** Angélica Morfa Morales
**Repositorio base:** [docker-tutorial de joseluisgs](https://github.com/joseluisgs/docker-tutorial)

---

## 💻 Entorno de Trabajo

Para la realización de estos ejercicios se preparó el siguiente entorno en Windows:
* **Docker Desktop** (Motor de contenedores).
* **WSL 2 con Ubuntu** (Subsistema de Windows para Linux).
* **Visual Studio Code** utilizando la terminal integrada y la opción de *Attach Shell* para interactuar directamente con los contenedores.

---

## 📂 Estado de los Ejercicios

| Directorio | Descripción de la Actividad | Estado |
|---|---|---|
| [`ejemplo-1/`](./ejemplo-1/) | Corrección de Dockerfile (PHP 8.2), construcción de imagen, despliegue y edición interna con `vim`. | ✅ Completado |
| `ejemplo-2/` | Interpretación y ejecución de scripts de automatización (`run.sh`). | ⏳ Pendiente |
| `ejemplo-3/` | (Reservado para futuras consignas). | ⏳ Pendiente |

---

## 🏗️ Estructura del Proyecto

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

```markdown
# Ejemplo 1: Edición dentro del Contenedor

## 🎯 Objetivo
Solucionar problemas de compatibilidad en el `Dockerfile`, levantar el contenedor web, instalar un editor de texto por terminal y modificar el archivo `index.html` en tiempo de ejecución.

## 🛠️ Solución de Problemas (Troubleshooting)
El repositorio original utilizaba la imagen `php:7.0-apache`. Al intentar trabajar dentro del contenedor, se producía un error de dependencias asociado a la librería **GLIBC**, ya que las versiones antiguas de PHP en Debian no son compatibles con las herramientas actuales.

**Solución:** Se actualizó el `Dockerfile` para utilizar una imagen moderna:
```dockerfile
FROM php:8.2-apache
COPY src/ /var/www/html/
