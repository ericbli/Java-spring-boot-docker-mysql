# spring-boot-docker-mysql
Spring Boot application running inside docker container linked with MySQL container.



## How to run it with Docker
Assume you already have Docker installed. See https://docs.docker.com/installation/.

First, clone the project and build locally:

~~~
git clone 
cd spring-boot-docker-mysql
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


