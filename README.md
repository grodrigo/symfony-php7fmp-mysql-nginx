#A docker-compose configuration to get mariadb, nginx and php7-fpm#

**Based almost all in [maxpou](https://github.com/maxpou/docker-symfony) repository but worth to take a look to [eko](https://github.com/eko/docker-symfony) and to [poroto82](https://github.com/poroto82/symfony-pgsql-nginx) repositories.**
I just reorganized some stuff and changed the db engine. 
Enjoy it  :thumbsup:

##USE##
- Install docker and docker-compose
- Clone this repo
- Clone your source application code. Use "application" as the folder name. 
- Copy .env.dist to .env and modify the example parameters to make them more accourate to your needs.
- docker-compose up -d
- localhost:8080 (or your host port)

---
Your folder structure must look like this:
- this_container
     | .env
     | application/
     | config/
     | docker-compose.yml
     | Dockerfile

##Usefull comands##
	```	
	#enter into the container
	docker-compose up -d	
	docker exec -it (name_of_your_folder)_php_1 bash
	
	#And now you are inside the php container, you can run for example:
	sf3 doctrine:schema:create
	sf3 assetic:dump
	```

	```
	#see your environment variables inside the running container
	docker inspect -f "{{ .Config.Env }}" {{foldername}}_php_1

	```

##NOTES:##
- There are three containers: db, nginx and php, another container for nginx named {{foldername}}{{service}}_1 each one, for example: myappname_php_1 and so on.

- You have installed nodejs 10.x and npm
But you may also need development tools to build native addons: apt-get install gcc g++ make
You can install Yarn package manager too, search for it if you need it.

- If you want to delete the content of a file like a log remember the
```cp /dev/null var/logs/prod.log```

##Additional notes:##
1- The application surce code must be in the same folder and cannot be relative due to the Dockerfile of the php service, it has a COPY command and it can't use relative paths.
2- In the case of the Nginx, we need a Dockerfile, but it's in the config directory because it doesn't have our last COPY problem and its folder is ferenced by build: config/nginx in the docker-compose.yml
3- COMPOSER_ALLOW_SUPERUSER is needed to run composer as superuser in the container.

