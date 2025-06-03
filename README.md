# Laravel - Docker Setup Guide

## Prerequisites
- Docker and Docker Compose installed on your system
- Git for cloning the repository

## Installation Steps

1. **Clone the repository**
   ```bash
    git clone https://github.com/pico-inno/project-pancake.git src
2. **Set up environment file**
   ```bash
    cp .env.docker src/.env
3. **Start Docker containers**
   ```bash
    docker-compose up -d --build
4. **Install dependencies**
   ```bash
    docker exec -it app composer install
5. **Generate application key**
   ```bash
    docker exec -it app php artisan key:generate
6. **Run database migrations**
   ```bash
    docker exec -it app php artisan migrate:fresh --seed
7. **Install Node.js dependencies**
   ```bash
    docker exec -it node npm install
8. **Build frontend assets**
   ```bash
    docker exec -it node npm run build
9. **Set file permissions**
   ```bash
    docker exec -it app bash -c "chown -R www-data:www-data /var/www/storage /var/www/bootstrap/cache"

    docker exec -it app bash -c "chmod -R 775 /var/www/storage /var/www/bootstrap/cache"
10. **Set Storage Link**
    ```bash
    docker exec -it app php artisan storage:link


*For Update*

1. **under directory**
    ```bash
    cd src

2. **update code**
    ```bash
    git pull origin main
3. **docker down**
    ```bash
    docker compose down
4. **docker up**
    ```bash
    docker compose up -d
