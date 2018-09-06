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

## 3. Enter the AMlaravel folder and copy env-example to .env
```
cp .env.example .env
```

## 4. Run the AM containers (the -d runs it in the background, --build makes sure it rebuilds the containers):
```
docker-compose up -d --build
```

## 5. To access the CLI:

Execute one of these from within the laradock folder:
```
docker-compose exec workspace bash
```
Or on Windows:
```
winpty docker-compose exec workspace bash
```
When it drops to the CLI within the workspace, navigate to the Laravel repo, install the components, generate a unique key and then migrate
```
cd AMlaravel
composer install
php artisan key:generate
php artisan migrate
```

## 6. A few more things...
We need to set our local DB to 'non strict mode', running the lines below on your db seems to do the job, there may be a better solution to this issue.
Without running this code, you will get a bunch of "'column_name' default value not set" errors.
```
SET GLOBAL sql_mode = 'NO_ENGINE_SUBSTITUTION';
SET SESSION sql_mode = 'NO_ENGINE_SUBSTITUTION';
```

You will need a dev.php file and a .gitignore file within AMDev, im unsure if these are things we can commit to the source code, so for now, we can share them between us.

You will also need to import the current db stuff to your new db, one of us can send you the file to import.

## 7. Open your browser and visit localhost:
- http://localhost/ for the existing site 
- http://localhost:81/ for the new Laravel site 
- http://localhost:82/ for PHPMyAdmin 

## That's it! enjoy :)

