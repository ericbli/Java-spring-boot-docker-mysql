# spring-boot-docker-mysql
Spring Boot application running inside docker container linked with MySQL container.



## How to run it with Docker
Assume you already have Docker installed. See https://docs.docker.com/installation/.

First, clone the project and build locally:

~~~
git clone 
cd Java-spring-boot-docker-mysql
mvn clean package docker:build
~~~

Run MySQL 5.6 in Docker container:

~~~
docker run --name demo-mysql -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=demo -e MYSQL_USER=demo_user -e MYSQL_PASSWORD=demo_pass -d mysql:5.6
~~~

Check the log to make sure the server is running OK:
~~~
docker logs demo-mysql
~~~

Run demo application in Docker container and link to demo-mysql:

~~~
docker run -p 8080:8080 --name demo-app --link demo-mysql:mysql -d eric/spring-boot-docker-mysql
~~~

You can check the log by
~~~
docker logs demo-app
~~~

Open http://192.168.99.100:8080/ in browser and you should see the message. 



Install:
---------------------------------------------------------------------
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"


sudo apt-get update

apt-cache policy docker-ce

sudo apt-get install -y docker-ce

______________________________________________________________________
#Check status
sudo systemctl status docker

-----------------------------------------------------------------------
sudo service docker start

docker --version
docker info
docker ps 
docker ps -a
docker ps -l
docker search ubuntu

docker images

docker run hello-world
docker pull ubuntu
docker run -it ubuntu
apt-get install -y nodejs



date
whoami
exit

#enter running docker 

docker attach cfb007d616b9



docker commit -m "added node.js" -a "Sunday eric li" d9b100f2f636 finid/ubuntu-nodejs
.......................................................................
docker stop 60504a2e1a08 
service docker stop
.........................................................................
To remove all containers that are NOT running

docker rm `docker ps -aq -f status=exited`

# Delete every Docker containers
# Must be run first because images are attached to containers


docker rm -f id1 id2 
..........................................................................
# Delete  Docker image
docker rmi -f id id2 id3


Dockerfile    Dockerfile
......................................
FROM node:7
WORKDIR /app
COPY package.json /app
RUN npm install
COPY . /app
CMD node index.js
EXPOSE 8082
.....................................
# cd to directory(with apps in)

docker build -t hello-system .




docker run --rm -it -p 1337:3000 --name hi7 hello-system
docker run --rm -it -p 8082:3000 --name hi7 hello-system
........................................................................................
运行wordpress MYSQL的命令 
docker run --rm  --name nmysql  -e MYSQL_ROOT_PASSWORD=root -e  MYSQL_DATABASE=blog -p 3306:3306 -d mysql
docker run   --name nmysql  -e MYSQL_ROOT_PASSWORD=root -e  MYSQL_DATABASE=blog -p 3306:3306 -d mysql


docker run --rm --detach --name nmysql  -e MYSQL_ROOT_PASSWORD=root -e  MYSQL_DATABASE=blog -p 3306:3306 -d mysql
docker run  --detach --name nmysql  -e MYSQL_ROOT_PASSWORD=root -e  MYSQL_DATABASE=blog -p 3306:3306 -d mysql
docker inspect nmysql | grep IPAddress
 
docker run --detach --name test-wordpress --link nmysql:mysql  -p 80:80 wordpress
open
http://192.168.99.100 to install wordpress
------------------------------------------------------------------------------------
docker run --rm -p 8080:8080 -t springio/gs-spring-boot-docker
http://192.168.99.100:8080/
-----------------------------------------------------------------------------------
#Check IP
docker-machine ip





1.Open cmd with admin rights.
2.Execute following command
docker-machine env --shell cmd default
3.you will receive following output

SET DOCKER_TLS_VERIFY=1

SET DOCKER_HOST=tcp://192.168.99.102:2376

SET DOCKER_CERT_PATH=C:\Users\DBashyal.docker\machine\machines\default

SET DOCKER_MACHINE_NAME=default

REM Run this command to configure your shell:

REM @FOR /f "tokens=*" %i IN ('docker-machine env --shell cmd default') DO @%i

4.Copy the highlighted line and execute on cmd

@FOR /f "tokens=*" %i IN ('docker-machine env --shell cmd default') DO @%i

5.Execute following command
docker ps





