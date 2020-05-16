# Docker SF4
With this project you can run all your projects Symfony, 4 or 5,  in a docker environment.

## Installation
### Step 1 : Download the docker project
The first thing to do is to download this git project on your server with the command :

```shell
$ git clone https://github.com/MikahDev/docker-symfony-4-5.git
```

### Step 2 : Download your symfony project
Download your Syfmony git project in the /app folder with the commands :
```shell
$ cd app/
$ git clone https://github.com/your-username/your-project
```

### Step 3 : Set the .env variables
All your files are here ! now we need to set all the variables in the .env file to run your app.
In first time copy the .env.dist in .env
```shell
$ cp .env.dist .env
```
Now set all the variable in your new .env file

| Variable | Description |
| ------------- |:-------------:|
| COMPOSE_PROJECT_NAME      | Name of the docker container |
| SYMFONY_PROJECT_NAME      | the folder name on your app/ directory |
| APP_ENV | Variable to know the env of your symfony app ("dev", "prod", "test") |
| MYSQL_DATABASE | The name of the docker database |
| MYSQL_PORT | The port use for mysql in docker |
| MYSQL_USER | The user of the docker database |
| MYSQL_PASSWORD | the password of the docker database |
| MYSQL_ROOT_PASSWORD | the root password of the docker database  |
| NGINX_PORT_HTTP |  Nginx port in docker for the http |
| NGINX_PORT_HTTPS | Nginx port in docker for the https |
| PMA_PORT | The PhpMyAdmin port in docker  |

### Step 4 : Build the docker-compose
Now you have set all your parameters, you can build your docker app with the command :
```shell
$ make -sC build
```

### Step 4 : Build the syfmony project
The docker project run well but we need to generate the symfony composer, the database and the webpack ressources.
Run  the commands :

```shell
$ make -sC composer
$ make -sC database-force
$ make -sC encore
```

Your project is now set and operational !

## Docker command
```shell
# You can run these individually
$ make -sC build
$ make -sC composer
$ make -sC database
$ make -sC encore
$ make -sC database-force
$ make -sC test
$ make -sC down
$ make -sC clean
```