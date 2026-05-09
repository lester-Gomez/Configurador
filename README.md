echo "Configurador variable de entorno"
echo "instalando php intelefes "
code --install-extension bmewburn.vscode-intelephense-client
echo "agregando php al path"
setx PATH "%PATH%;C:\APPS\xampp\php"
echo "cinfigurar composer"
echo "descargando composer"
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
echo "verificando composer"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'c8b085408188070d5f52bcfe4ecfbee5f727afa458b2573b8eaaf77b3419b0bf2768dc67c86944da1544f06fa544fd47') { echo 'Installer verified'.PHP_EOL; } else { echo 'Installer corrupt'.PHP_EOL; unlink('composer-setup.php'); exit(1); }"
echo "instalando composer"
php composer-setup.php
echo "eliminando instalador"
php -r "unlink('composer-setup.php');"
echo "renombrando composer"
ren "composer.phar" "composer"
echo "Inisiando configurasion de prollecto"
echo "creando composer"
composer init
echo "creando carpeta public"
md public
echo "Insalando flihtphp"
composer require flightphp/core
echo "creando index php"
echo ^<?php declare(strict_types=1); ^?> > ./public/index.php
echo "inializando servidor de apollo"
php -S localhost:8000 -t ./public/
echo "Finalizado"
