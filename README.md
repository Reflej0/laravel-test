# laravel-test
Prueba con Laradock, MySQL, MongoDB, proyecto de prueba de bestmomo.

# Comandos utiles o pasos
---------------------

 1) Seguir pasos https://laradock.io/, es decir clonar el repo, mandar el docker-compose up con los componentes que se desean instalar y cambiar el nombre de env-example a .env osea un archivo oculto de extension .env en linux.
 2) En laradock/nginx/sites estan las configuraciones por defecto del nginx, cambiar el archivo de laravel a default.conf
 3) El archivo .env tiene la configuracion de la base de datos, los paths de donde va a estar el proyecto, en workspace los modulos adicionales como el mongodb, y en mysql la configuracion especifica para mysql.
 4) Como la linea APP_CODE_PATH_HOST=../ tiene ../ se espera que el proyecto de Laravel este fuera de la carpeta laradock.
 5) Bajar el ejemplo https://github.com/bestmomo/laravel5-example y poner afuera de la carpeta laradock, por el punto anterior, aca se puede bajar cualquier proyecto yo elegi el anterior de ejemplo.
 6) Una vez ejecutado el **docker-compose up -d nginx mysql phpmyadmin redis workspace mongo** (en la raiz de la carpeta laradock) ejecutar el **docker-compose exec workspace bash** y despues hacer **cd public** (o la carpeta donde este el proyecto)
 7) **composer install php artisan key:generate php artisan migrate --seed php artisan vendor:publish php artisan serve**
 8) Sí llegan a existir errores con la base de datos en php artisan migrate -seed o al conectarse con el localhost:8080 revisar el .env pero de la carpeta public (existen dos .env uno del laradock y otro del proyecto).
 9) Sí se necesitarian crear usuarios para entrar a la base de datos: **docker-compose exec mysql bash** y despues **mysql -u root -p** password root
 10) Usuarios por defecto:  
 ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';  
ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'root';  
ALTER USER 'default'@'%' IDENTIFIED WITH mysql_native_password BY 'secret';
11) Sí después del **php artisan serve** el localhost:8000 no funciona, pero lo demas sí (osea el localhost:8080 y el localhost al menos tira forbidden) se puede optar por https://stackoverflow.com/questions/48719658/run-laravel-project-in-localhost (la respuesta que tiene 3 pasos (renombrar archivo, mover el .htaccess y chmod a public).

Cualquier cosa ver los archivos del repositorio, especialmente los de configuracion.

# Links para solucion de errores
---------------------
https://stackoverflow.com/questions/34681541/laravel-5-2-artisan-optimize-php-strip-whitespace-failed-to-open-stream-no-ch
https://stackoverflow.com/questions/52364415/the-server-requested-authentication-method-unknown-to-the-client-php
https://stackoverflow.com/questions/48719658/run-laravel-project-in-localhost  
https://stackoverflow.com/questions/35394230/sqlstatehy000-2002-connection-refused-within-laravel-homestead
