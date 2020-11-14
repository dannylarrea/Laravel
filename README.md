### Instalación Laravel macOS
1. https://laravel.com/docs/8.x#installing-laravel ==> Instalar composer: https://getcomposer.org/download/
  ```
  php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
  php -r "if (hash_file('sha384', 'composer-setup.php') === 'c31c1e292ad7be5f49291169c0ac8f683499edddcfd4e42232982d0fd193004208a58ff6f353fde0012d35fdd72bc394') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
  php composer-setup.php
  php -r "unlink('composer-setup.php');”
  sudo mv composer.phar /usr/local/bin/composer
  // verificamos que todo está ok después de la instalación:
  composer
  ```

2. https://laravel.com/docs/8.x#via-composer-create-project
  ```
  composer create-project --prefer-dist laravel/laravel blog
  cd blog
  php artisan serve
  ```

# Como subir un proyecto local a github.
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
