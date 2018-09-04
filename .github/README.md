Let’s see how easy it is to install NGINX, PHP, Composer, MySQL, Redis and Beanstalkd:

## 1. Clone Laradock next to AMDev and AMLaravel:
```
git clone https://github.com/AccountancyManager/AMdev.git
git clone https://github.com/AccountancyManager/AMlaravel.git
git clone https://github.com/AccountancyManager/laradock.git
```
Your folders next to each other should look like:
- AMdev
- AMlaravel
- laradock

## 2. Enter the laradock folder and copy env-example to .env
```
cp env-example .env
```

## 3. Run the AM containers (the -d runs it in the background, --build makes sure it rebuilds the containers):
```
docker-compose up -d --build
```

## 4. Open the Laravel .env file and set the following:
```
DB_HOST=mysql
DB_DATABASE=accountancymanager
DB_USER=root
DB_PASSWORD=root
DB_PORT=3306

REDIS_HOST=redis

QUEUE_HOST=beanstalkd
```

## 5. Open your browser and visit localhost:
- http://localhost/ for the existing site 
- http://localhost:81/ for the new Laravel site 
- http://localhost:82/ for PHPMyAdmin 

## 6. To access the CLI:
```
docker-compose exec workspace bash
```
on Windows:
```
winpty docker-compose exec workspace bash
```
## That's it! enjoy :)

