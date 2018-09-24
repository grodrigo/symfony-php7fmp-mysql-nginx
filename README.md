*A docker-compose configuration to get mariadb, nginx, php7-fpm*


**Based almost all in https://github.com/maxpou/docker-symfony but it's good to take a view to https://github.com/eko/docker-symfony and https://github.com/poroto82/symfony-pgsql-nginx**
I just reorganized some stuff and change db engine
Enjoy it

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
cp /dev/null var/logs/prod.log


