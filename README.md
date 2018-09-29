#A docker-compose configuration to get mariadb, nginx and php7-fpm#

**Based almost all in [maxpou](https://github.com/maxpou/docker-symfony) repository but worth to take a look to [eko](https://github.com/eko/docker-symfony) and to [poroto82](https://github.com/poroto82/symfony-pgsql-nginx) repositories.**
I just reorganized some stuff and changed the db engine. 
Enjoy it  :thumbsup:

##USE##
- Install docker and docker-compose
- Clone this repo
- Copy .env.dist to .env and modify the example parameters to make them more accourate with your needs. Be sure to set the environment variable SYMFONY_APP_PATH to your application folder.
*(It could be in the same directory as in the example or a relative path to where you want)*
- docker-compose up -d
- localhost:8080 (or your host port)

##Usefull comands##
	```
	#see your environment variables inside the running container
	docker inspect -f "{{ .Config.Env }}" {{foldername}}_php_1
	
	#enter into the container
	docker-compose up -d	
	docker exec -it (name_of_your_folder)_php_1 bash
	```
And now you are inside the php container, you can run for example:
	```
	sf3 doctrine:schema:create
	sf3 assetic:dump
	```

##NOTES##
- You have installed nodejs 10.x and npm
But you may also need development tools to build native addons: apt-get install gcc g++ make
You can install Yarn package manager too, search for it if you need it.

- There are three containers: db, nginx and php, another container for nginx named {{foldername}}{{service}}_1 each one, for example: myappname_php_1 and so on.

- If you want to delete the content of a file like a log remember the
```cp /dev/null var/logs/prod.log```


