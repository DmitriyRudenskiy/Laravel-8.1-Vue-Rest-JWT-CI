# 0. установка
- запускаем сборку на специальных портах 8081 и 3307
APP_PORT=8081 MYSQL_PORT=3307 docker-compose up -d --build

- создаём проект если не существует
docker run --rm --interactive --tty \
  --volume $PWD:/app \
  composer create-project --prefer-dist laravel/laravel backend1 "8.*"
  
- проверяем
php artisan --version
  
  
#1. подключаем статический анализ
docker run --rm --interactive --tty \
  --volume $PWD:/app \
  composer require nunomaduro/phpinsights --dev

php composer.phar require nunomaduro/phpinsights --dev
  
//
PHP CodeSniffer Config installed_paths set to ../../slevomat/coding-standard,../../object-calisthenics/phpcs-calisthenics-rules/src
  
  
php artisan vendor:publish --provider="NunoMaduro\PhpInsights\Application\Adapters\Laravel\InsightsServiceProvider"
!!!Unable to locate publishable resources
>>>
php artisan clear-compiled
composer dumpautoload
>>>

запускаем
php artisan insights
  

 "tymon/jwt-auth": "1.0.*"
 php artisan --version


Discovered Package: facade/ignition
Discovered Package: fideloper/proxy
Discovered Package: fruitcake/laravel-cors
Discovered Package: laravel/tinker
Discovered Package: nesbot/carbon
Discovered Package: nunomaduro/collision




apk add --update libbz2 libpng-dev libwebp libjpeg-turbo libxpm freetype


docker run --rm --interactive --tty \
  --volume $PWD:/app \
  composer require tymon/jwt-auth
