# Docker SF4
Download the git project docker-sf4
Go to the folder /app and download your symfony git project
Copy the .env.dit at .env for the local configuration
cp .env.dist .env
Setup  your .env with your parameters
Build your docker compose
sudo make -s build
Initialize your symfony project with composer
sudo make -s composer
Create your database schema
sudo make -s database-force
if you use Webpack encore, build the file
sudo make -s encore

## Generate ssl certificat (self signed):
   
```shell
sudo openssl genrsa -out docker/dev/nginx/app_ssl.key 4096
sudo openssl req -new -x509 -days 365 -key docker/dev/nginx/app_ssl.key -out docker/dev/nginx/app_ssl.crt
```

## Git project download
For download your symfony project,  you need to add the file in /app with the command :
```shell
cd app/ >> git clone [project git url] .
```

## Docker command
```docker
# You can run these individually
$ make -sC docker/dev/ build
$ make -sC docker/dev/ composer
$ make -sC docker/dev/ database
$ make -sC docker/dev/ test
$ make -sC docker/dev/ down
$ make -sC docker/dev/ clean
    
# This will cover all the command listed above in one go
$ make -sC docker/dev/ all
```