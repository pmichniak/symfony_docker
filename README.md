# Symfony 5 Docker
> Docker Compose Symfony 5 - for microservices, console application or API

1 - Clone repository:
```dotenv
git clone git@github.com:pmichniak/symfony_docker.git
```

2 - Copy .env.dist to .env and paste your credentials in .env
```dotenv
cp .env.dist .env
```

## Installation
3 - Start the docker-compose
```bash
docker-compose up -d
```

4 - Install all the dependencies
```bash
docker exec -it -u 1000 symfony_php_fpm /bin/sh
composer install
``` 

## Run the application

 **[http://symfony.localhost](http://symfony.localhost)**

Entering the containers
```bash
docker exec -it -u 1000 symfony_php_fpm /bin/sh
docker exec -it -u 1000 symfony_mysql /bin/sh
docker exec -it -u 1000 symfony_nginx /bin/sh
