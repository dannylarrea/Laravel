### Instalación laravel
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
