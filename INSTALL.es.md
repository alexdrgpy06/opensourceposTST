## Requisitos del Servidor

-   **PHP:** Se soportan las versiones de `8.1` a `8.4`. **NO** se soportan versiones de PHP `≤7.4`. Ten en cuenta que PHP necesita tener las siguientes extensiones instaladas y habilitadas: `php-json`, `php-gd`, `php-bcmath`, `php-intl`, `php-openssl`, `php-mbstring`, `php-curl` y `php-xml`.
-   **MySQL/MariaDB:** Se soporta MySQL `5.7` o superior. También se soporta MariaDB `10.x`, que podría ofrecer un mejor rendimiento.
-   **Servidor Web:** Se soporta Apache `2.4`. Nginx también debería funcionar correctamente.

## Instalación Local (Método Tradicional)

Esta guía te ayudará a instalar Open Source Point of Sale en tu propio ordenador para desarrollo o pruebas.

### Paso 1: Configurar un Entorno de Servidor Local

Si no tienes un servidor web con PHP y MySQL en tu ordenador, la forma más sencilla de empezar es instalando un paquete de software como [XAMPP](https://www.apachefriends.org/es/index.html), [WAMP](https://www.wampserver.com/en/) o [MAMP](https://www.mamp.info/en/mamp/). Estos paquetes incluyen todo lo necesario: Apache, PHP y MariaDB/MySQL.

1.  **Descarga e instala** uno de los paquetes mencionados.
2.  **Inicia los servicios** de Apache y MySQL desde el panel de control del software que instalaste.

### Paso 2: Descargar OSPOS

1.  Ve a la [página de releases de GitHub](https://github.com/opensourcepos/opensourcepos/releases).
2.  Descarga la última versión estable (el archivo `.zip` o `.tar.gz`). **No clones el repositorio directamente** a menos que sepas cómo construir el proyecto, ya que no funcionará sin un paso de compilación.

### Paso 3: Configurar la Base de Datos

1.  Abre tu navegador y ve a `http://localhost/phpmyadmin` (esta es la URL por defecto para XAMPP y WAMP).
2.  Crea una nueva base de datos. Puedes llamarla `ospos` o como prefieras.
3.  Selecciona la base de datos que acabas de crear.
4.  Haz clic en la pestaña "Importar".
5.  Haz clic en "Seleccionar archivo" y busca el archivo `database.sql` que se encuentra dentro de la carpeta `app/Database/` en los archivos de OSPOS que descargaste.
6.  Haz clic en "Continuar" para importar la estructura y los datos iniciales de la base de datos.

### Paso 4: Instalar los Archivos de OSPOS

1.  Descomprime el archivo de OSPOS que descargaste.
2.  Copia la carpeta descomprimida (debería llamarse algo como `opensourcepos-3.4.0`) en el directorio raíz de tu servidor web.
    -   En **XAMPP**, este directorio suele ser `C:\xampp\htdocs\` en Windows.
    -   En **WAMP**, es `C:\wamp64\www\`.
    -   Puedes renombrar la carpeta a algo más simple, como `ospos`.

### Paso 5: Configurar la Conexión a la Base de Datos

1.  Dentro de la carpeta de OSPOS, busca el archivo `.env-example` y renómbralo a `.env`.
2.  Abre el archivo `.env` con un editor de texto.
3.  Busca la sección de configuración de la base de datos y modifica las credenciales para que coincidan con tu configuración local. Por lo general, en una instalación de XAMPP o WAMP, el usuario es `root` y la contraseña está vacía.

    ```
    database.default.hostname = localhost
    database.default.database = ospos
    database.default.username = root
    database.default.password =
    database.default.DBDriver = MySQLi
    ```

### Paso 6: Primer Inicio de Sesión

1.  Abre tu navegador y ve a la carpeta `public` de tu instalación. Por ejemplo: `http://localhost/ospos/public/`.
2.  Inicia sesión con las credenciales por defecto:
    -   **Usuario:** `admin`
    -   **Contraseña:** `pointofsale`
3.  Si todo funciona correctamente, ¡ya estás listo!

### Solución de Problemas Comunes

-   **Error `system folder missing`:** Esto significa que clonaste el repositorio en lugar de descargar una release. Sigue las instrucciones del Paso 2.
-   **La página no se carga (Error 404 o 500):**
    -   Asegúrate de que el módulo `mod_rewrite` de Apache esté activado.
    -   Verifica que los servicios de Apache y MySQL se estén ejecutando.
    -   Revisa los archivos de log de errores de Apache para obtener más detalles.
-   **Inicio de sesión incorrecto:** Asegúrate de haber importado el archivo `database.sql` correctamente y de que las credenciales en tu archivo `.env` son correctas.

## Instalación Local usando Docker

Si tienes [Docker](https://www.docker.com/) instalado, puedes usarlo para desplegar OSPOS fácilmente. Esta configuración es ideal para el desarrollo, ya que evita problemas de configuración del entorno.

**¡Atención! Esta configuración no es adecuada para producción. Cambia las contraseñas por defecto antes de exponer los contenedores públicamente.**

1.  Clona el repositorio o descarga los archivos.
2.  Abre una terminal o línea de comandos en la carpeta raíz del proyecto.
3.  Ejecuta el siguiente comando para iniciar los contenedores:

    ```
    docker-compose up
    ```

4.  Una vez que los contenedores se hayan creado e iniciado, puedes acceder a OSPOS en `http://localhost`.
