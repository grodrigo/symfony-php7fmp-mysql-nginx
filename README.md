*A docker-compose configuration to get mariadb, nginx, php7-fpm*


**Based almost all in https://github.com/maxpou/docker-symfony but worth to take a look to https://github.com/eko/docker-symfony and to https://github.com/poroto82/symfony-pgsql-nginx**
I just reorganized some stuff and changed the db engine.  
Enjoy it

**USE:**
Clone this repo to a folder and create an application folder on it. Then, in the application folder clone your project.
(change the app folder if you want in the .env file)
copy .env.dist to .env and change it the way you like it.
```cp .env.dist .env

docker-compose build
docker-compose up

docker exec -it (name_of_your_folder)_php_1 bash
composer update
sf doctrine:schema:create
sf assetic:dump
install optipng jpegoptim```

node isn't inside the container. Run it outside.


TODO:
Change var/logs and cache permissions, and var/sessions
Run composer update
Run create schema
console assetic:dump
install node
install optipng, jpegoptim

You can run any of the commands that you need just by doing:  

docker exec -it name_of_your_folder_php_1 bash
and you are in.

There are another container for nginx and another one to mysql

If you want to delete the content of a file like a log remember the
```cp /dev/null var/logs/prod.log```


