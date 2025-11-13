# Compilando OSPOS

## Solo para Desarrolladores y Entusiastas

Si eres un desarrollador y necesitas añadir funcionalidades únicas a OSPOS, puedes descargar el código fuente desde el repositorio de GitHub y realizar tus cambios. Si es un cambio realmente genial que podría beneficiar a otros, te pedimos que consideres contribuirlo al proyecto.

Después de hacer tus cambios, necesitarás "COMPILARLO" para añadir todos los componentes necesarios que OSPOS requiere para ser una aplicación completamente funcional.

Este documento explica el proceso de "Cómo Compilar".

El objetivo aquí es configurar el proceso de compilación para que la compilación real sea lo más simple posible.

El proceso de compilación utiliza las herramientas "npm" y "gulp" para unir todo.

## Prerrequisitos

-   Instala la última versión de **NPM** (probado con la versión 9.4.2). NPM se instala junto con [Node.js](https://nodejs.org/es/).
-   Instala la última versión de **Composer** (probado con la versión 2.5.1). Puedes descargarlo desde [getcomposer.org](https://getcomposer.org/).

## El Proceso de Compilación

1.  Descarga el código desde la rama `master` que se encuentra en [https://github.com/opensourcepos/opensourcepos/tree/master](https://github.com/opensourcepos/opensourcepos/tree/master). Haz clic en el botón "Code" y luego en "Download ZIP".
2.  Descomprime el archivo y copia el contenido en tu carpeta de trabajo.
3.  Inicia una sesión de terminal (línea de comandos) desde la raíz de tu carpeta de trabajo.
4.  Introduce los siguientes tres comandos en secuencia, uno después del otro:
    -   `composer install` (Instala las dependencias de PHP)
    -   `npm install` (Instala las dependencias de JavaScript/Node.js)
    -   `npm run build` (Ejecuta el proceso de compilación)

¡Eso es todo!

**Nota:** Si recibes mensajes similares a `'codeigniter4/framework v4.3.1 requires ext-intl'`, esto indica que no tienes la extensión `intl` habilitada en tu archivo `php.ini`. Deberás habilitarla para continuar.

Después de que las tareas de compilación se completen, si ya tienes una base de datos configurada y una copia preconfigurada de tu archivo `.env`, simplemente colócalo en la raíz de la carpeta de trabajo. Deberías estar listo para empezar.

Si no tienes una base de datos existente (y actualizada), entonces necesitarás continuar desde este punto con las instrucciones de instalación estándar. La compilación te deja con una versión ejecutable de OSPOS lista para ser instalada.

### Entorno de Desarrollo con Docker

Usar Docker para el desarrollo tiene la ventaja de que todas las dependencias de la aplicación están contenidas dentro del entorno de Docker. Durante el desarrollo, queremos tener una versión en vivo del código en el contenedor cuando lo editamos. Esto se logra montando la carpeta de la aplicación dentro de `/app` del contenedor de Docker.

Los permisos de archivo para el repositorio en el contenedor deben ser los mismos que en el anfitrión. Por eso tenemos que iniciar el proceso de PHP en Docker con el `uid` actual del anfitrión.

```bash
export USERID=$(id -u)
export GROUPID=$(id -g)
docker-compose -f docker-compose.dev.yml up
```

## El Resultado

La compilación crea una versión de desarrollo de una instancia ejecutable de OSPOS. Contiene una gran cantidad de herramientas y archivos de desarrollo que **no deben ser desplegados en un entorno de producción**.

Nuevamente, el resultado de esta compilación NO es algo que deba usarse para producción.

Sin embargo, los archivos zip y tar, que se encuentran en la carpeta `dist` en la raíz del proyecto, se crean como parte del proceso de compilación y pueden usarse para desplegar una instancia de OSPOS para ***pruebas de producción***.

**Solo las releases oficiales deben usarse para producción real.** Existe un riesgo significativo de fallos si eliges desplegar una rama de desarrollo o incluso la rama `master` que el equipo de desarrollo no ha aprobado.

Buena suerte con tu compilación. Por favor, informa de cualquier problema que encuentres.
