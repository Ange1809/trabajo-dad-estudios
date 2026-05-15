# Prácticas de Docker - Diseño y Arquitectura de Despliegue

Repositorio destinado a la documentación y resolución de actividades prácticas de la materia **Diseño y Arquitectura de Despliegue (DAD)**. El enfoque principal es el aprendizaje de la contenedrización, gestión de imágenes y orquestación de servicios.

**Estudiante:** Angélica Morfa Morales  
**Repositorio base:** [docker-tutorial de joseluisgs](https://github.com/joseluisgs/docker-tutorial)

---

## Entorno de Desarrollo

Para la ejecución y testeo de los contenedores se utilizó la siguiente configuración:
* **Motor de contenedores:** Docker Desktop.
* **Subsistema Linux:** WSL 2 (Ubuntu) en entorno Windows.
* **IDE:** Visual Studio Code (Terminal integrada y extensión Docker).

---

## Resumen de Actividades

* **[Ejemplo 1](./ejemplo-1/) (Completado):** Actualización del Dockerfile (PHP 8.2), despliegue web y edición en caliente mediante Vim.
* **[Ejemplo 2](./ejemplo-2/) (Completado):** Análisis y ejecución de scripts de automatización (`run.sh`) para el despliegue de imágenes.
* **[Ejemplo 3](./ejemplo-3/) (Completado):** Evaluación técnica sobre la portabilidad de scripts de sistema operativo frente a estándares agnósticos.
* **[Ejemplo 7](./ejemplo-7/) (Completado):** Implementación de un entorno multi-contenedor (LEMP) utilizando Docker Compose.

---

## Estructura del Proyecto

```text
📦 trabajo-dad-estudios
 ┣ 📜 README.md
 ┣ 📂 ejemplo-1
 ┃ ┣ 📜 README.md
 ┃ ┗ 📂 screenshots
 ┣ 📂 ejemplo-2
 ┃ ┣ 📜 README.md
 ┃ ┗ 📂 screenshots
 ┣ 📂 ejemplo-3
 ┃ ┣ 📜 README.md
 ┃ ┗ 📂 screenshots
 ┗ 📂 ejemplo-7
   ┣ 📜 README.md
   ┗ 📂 screenshots

---

### 2. Archivo Ejemplo 2 (`ejemplo-2/README.md`)

```markdown
# Ejemplo 2: Automatización mediante Scripts de Shell

## Objetivo
Interpretar y ejecutar el archivo `run.sh` para automatizar la construcción de la imagen y el lanzamiento del contenedor, reduciendo la carga de comandos manuales en la terminal.

## Ejecución
Se analizó el flujo del script, el cual agrupa las instrucciones `docker build` y `docker run`. El despliegue se realizó satisfactoriamente desde la terminal de PowerShell utilizando el intérprete de Bash.

![Despliegue Ejemplo 2](./screenshots/01-deploy-ejem02.png)

# Ejemplo 3: Análisis de Portabilidad en Scripts de S.O.

## Objetivo
Evaluar el uso de scripts de sistema operativo para la orquestación de contenedores y los inconvenientes que esto conlleva en entornos distribuidos.

## Evaluación Técnica
El uso de archivos `.sh` o `.bat` presenta limitaciones críticas:
1. **Falta de Portabilidad:** Los scripts de shell dependen del intérprete del sistema operativo (Bash/Unix), lo que genera fallos en entornos Windows nativos.
2. **Escalabilidad:** A medida que el entorno crece, el mantenimiento de scripts secuenciales se vuelve complejo frente a soluciones declarativas.

**Conclusión:** Se recomienda el uso de **Docker Compose** para garantizar que la infraestructura sea agnóstica al sistema operativo del host.

![Despliegue Ejemplo 3](./screenshots/01-deploy-ejem03.png)

# Ejemplo 7: Orquestación con Docker Compose

## Objetivo
Implementar un entorno complejo que incluye un servidor Nginx, PHP 8.2, MariaDB y phpMyAdmin, gestionados como un conjunto de servicios interconectados.

## Resolución de Conflictos
Durante el despliegue se resolvieron dos incidentes críticos:
1. **Conflicto de Nombres:** Existencia de contenedores previos con el nombre `mariadb`. Se procedió a su remoción mediante `docker rm -f`.
2. **Conflicto de Puertos:** El puerto 8080 estaba ocupado por servicios de prácticas anteriores. Se liberó el puerto para permitir el bind del servicio Nginx.

## Resultado
El entorno se levantó exitosamente utilizando `docker compose up -d`, permitiendo la persistencia de datos y la administración web de la base de datos.

![Despliegue Ejemplo 7](./screenshots/01-deploy-ejem07.png)
