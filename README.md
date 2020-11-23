# Instalación Laravel macOS (Laravel 8.x | 2020)
1. Instalación composet
> https://laravel.com/docs/8.x#installing-laravel ==> Instalar composer: https://getcomposer.org/download/
>  ```
>  php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
>  php -r "if (hash_file('sha384', 'composer-setup.php') === 'c31c1e292ad7be5f49291169c0ac8f683499edddcfd4e42232982d0fd193004208a58ff6f353fde0012d35fdd72bc394') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
>  php composer-setup.php``
>  php -r "unlink('composer-setup.php');"
>  sudo mv composer.phar /usr/local/bin/composer
>  // verificamos que todo está ok después de la instalación:
>  composer
>  ```

2. "Testear" Laravel creando un primer proyecto
>   https://laravel.com/docs/8.x#via-composer-create-project
>   ```
>   composer create-project --prefer-dist laravel/laravel blog
>   cd blog
>   php artisan serve
>   ```
- - - -
## Artisan CLI (Artisan is the name of the command-line interface included with Laravel)
```
// Displaying Your Current Laravel Version
php artisan --version

// Crear un proyecto con Laravel
composer create-project --prefer-dist laravel/laravel projectname

// Iniciar el vhost (dejar la ejecución en VSC siempre en segundo plano)
php artisan serve

// Crear modelo (model), controlador (-c) (relación entre ambos: -r abreviatura de --resource) y migración (-m). Por convenio el nombre del modelo ha de ir con la primera letra en mayúscula, en ingles y en singular.
php artisan make:model Author -mcr

// Crear controlador (controller)
php artisan make:controller ModelController

// Running Migrations
php artisan migrate

// Roll Back & Migrate
php artisan migrate:refresh

// Drop All Tables & Migrate
php artisan migrate:fresh
```

**INFO Modelo, controlador (relación entre ambos) y migración**
* https://laravel.com/docs/8.x/eloquent
* https://laravel.com/docs/8.x/controllers
* https://laravel.com/docs/8.x/controllers#resource-controllers

Puntos a tener en cuenta:
* Creamos la base de datos en phpMyAdmin (nombre igual al directorio del proyecto, p. ex.: bd_projectname)
* Añadimos la base de datos a la conexión. Editar el fichero: `vendor/.env`
> ```
> DB_CONNECTION=mysql
> DB_HOST=127.0.0.1
> DB_PORT=3306 /* igual al del servicio MySQL del XAMPP */
> DB_DATABASE=data_base
> DB_USERNAME=root
> DB_PASSWORD=
> ```

**INFO Migraciones (creación base de datos)**

https://laravel.com/docs/8.x/migrations
https://laravel.com/docs/8.x/migrations#running-migrations

**INFO Seeders**
* https://laravel.com/docs/8.x/seeding

**INFO Vista `(ruta->controller->view)`**
* https://laravel.com/docs/8.x/controllers


**INFO Añadir ficheros: imágenes, .css, etc.**
* https://laravel.com/docs/8.x/helpers#method-asset
> asset() - The asset function generates a URL for an asset using the current scheme of the request (HTTP or HTTPS):
> $url = asset('img/photo.jpg');

```HTML
<!-- p. ex.: para utilizar una hoja de estilos styles.css esta se debe de ubicar dentro de la ruta public/css/styles.css y se debe de llamar desde el .php de la siguiente forma: -->
<link rel="stylesheet" type="text/css" href="{{asset('css/styles.css')}}">
```
**INFO CRUD**
* https://laravel.com/docs/8.x/database
* https://laravel.com/docs/8.x/queries#selects
* https://richos.gitbooks.io/laravel-5/content/

# Algunos errores en macOS
**Error 1. Página por defecto de inicio no se visualiza (contiene error)**
> https://stackoverflow.com/questions/62801389/laravel-voyager-setup-error-file-put-contents
> in vendor\laravel\framework\src\Filesystem\Filesystem.php file change below line change `LOCK_EX` to `LOCK_SH`

**Error 2. Migraciones no se ejecutan en VSC**
> ```
> // En la aplicación de XAMPP clicamos GENERAL > Open Terminal y ejecutamos los siguientes comandos:
> root@debian:~# cd ..
> root@debian:/# cd opt/lampp/htdocs/www/Proyectos/bookstore/
> root@debian:/opt/lampp/htdocs/www/Proyectos/bookstore# php artisan migrate
> ```

**Error 3. Añadir en los controladores (en aquellos que realizan queries) la siguiente línea:**
> `use Illuminate\Support\Facades\DB;`

**Error 4. The stream or file “/storage/logs/laravel.log” could not be opened: failed to open stream: Permission denied**
> ```
> // Permisos (chmod ...) a los directorios:`
> chmod -R 775 resources/
> chmod -R 777 storage/
> ```

**Error 5. Access denied for user root@localhost | PHP | Laravel (Connection refused)**
> Crear un usuario específico para la base de datos que se está usando (p. ex.: `danny`) y en el fichero `.env` asignar el host de la base de datos correctamente (en mi caso `DB_HOST=192.168.64.2`)

**Error 6. Añadir rutas en el fichero: app/Http/Middleware/VerifyCsrfToken.php**
> * https://www.positronx.io/laravel-ajax-example-tutorial/

# Subir un proyecto local a GitHub
### desde la web de github
Creamos un nuevo repositorio en <https://github.com>. Le damos nombre, descripción, seleccionamos si va a ser un proyecto publico o privado si es el caso, y dejamos el check de crear README sin marcar.
Le damos a __crear repositorio__ y con esto ya tenemos el repositorio donde alojaremos nuestro proyecto.
### desde la terminal del equipo donde esta el proyecto que queremos subir a github
Nos vamos a la carpeta del proyecto y ejecutamos estos comandos.
```
git init

git add .

git commit -m "first commit"

git remote add origin https://github.com/NOMBRE_USUARIO/NOMBRE_PROYECTO.git

git push -u origin master

```
