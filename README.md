# setup-laravel_docker_mysql


$ gitclone

$ composer create-project laravel/laravel demo

# Construir imagem docker com laravel

$ docker compose up -d --build

# Verificar os containers ativos:

$ docker container ls

$ docker exec setup-php php artisan config:cache

$ docker exec setup-php composer install

$ docker exec setup-php php artisan migrate
