## ### Docker basic commands
Assume docker is already installed

$docker images
to see all the images in docker 

to get image from remote repo
#docker pull image-name:version

#docker pull alpine
it will pull latest version from docker hub reg

#docker rmi imageid/imagename:version
$docker rmi alpine:latest

we can not remove images if a container related to that image is running.

first we need to stop/terminate the containers related to that image and then remove the image.
we can remove multiple images in one single command.
$docker rmi id1 id2 id3 etc

first get list of image ids
$docker images -q 

$docker rmi $(docker images -q)

$docker inspect imageid

### How to run docker images?
$docker run -d -p 9090:80 httpd:latest

$docker run -d -p 9090:80 --name=myweb httpd:latest

if you did not provide a dummy name then docker will provide some name to the container.

### How to check the running containers on this host?
ans: the below command is used to list all running containers on this host.
$docker ps


### How to access the containers by using web-browsers?
ans: 
http://localhost:port-from-host

$docker ps -a

$docker stop containerid/containername

$docker start containerid/containername

$docker restart containerid/containername

### How to remove the container?
$docker rm containerid/containername space list.

we can not remove a container it is in running state.

force remove 

$docker rm -f containerid/name

### How to remove all container in one single command?

docker ps -aq   q will return only container ids.

$docker rm $(docker ps -aq)

### How will you get container prompt?

#docker exec -it  containerid/name /bin/bash

to come out of the container we use exit.

$docker logs containername/id

$docker inspect container-name/id
mac addr
ip
workdir
etc

### How to build images by using docker file?
ams
let us create a work space.
mkdir dockerdemo
cd dockerdemo
sample project clone from git hub
git clone https://github.com/javahometech/node-app

docker run -d -p 90:8080 --name=nodeapp nodeapp:1.0

docker ps
### example of docker file:
Docker file
FROM ubuntu:16.04
LABEL maintainer='Java Home Cloud' \
      employee_name = 'Hari Kammana' \
      version = 1.0.0
RUN apt-get update -y
RUN apt-get install apache2 -y
RUN apt-get install wget -y
RUN apt-get install unzip -y

WORKDIR /tmp

RUN wget https://github.com/javahometech/javahome-app/archive/master.zip

RUN unzip master.zip

#Apache server deployment directory is /var/www/html

RUN cp -r javahome-app-master/* /var/www/html

EXPOSE 80

CMD ["apachectl", "-D", "FOREGROUND"]

Build the image and lets us run the container.
cd /docker/youtube

$docker build -t kammana/app:1.0.0 .
....
....
Sucessfully build <image-id>
Sucessfully tagged kamana/app:1.0.0

run the docker image now
$docker run -d -p 8080:80 <image-id>


### Entry Point vs CMD
CMD is executed at runtime
### ### example:
FROM ubuntu:16.04
CMD echo 'Welcome to docker'

docker build -t app .

### how to run the container from mage
docker run -it <imageid>
docker run -it <imageid> echo 'Welcome to AWS'

### Can we use multiple command instructions in the docker file?
ans: yes let us see.

vi Dockerfile
FROM ubuntu:16.04
CMD echo 'Welcome to docker'
CMD echo 'Welcome to Python'
only new one will be considered
build the docker image 
docker build -t app .
run the image
docker run -it <image-id>

### entry point instruction is runtime instruction.

vi dockerfile
FROM ubuntu:16.04
ENTRYPOINT ["echo","Hi Docker"]
docker build -t app .
docker run -it <image-id>

dcoker run -it <image-id> echo 'Hi Hari'
you will see appended.$docker run -d -

FROM ubuntu:16.04
ENTRYPOINT ["echo"]
CMD ["Hi Docker"]

CMD is input for entry point.
docker build -t app .
docker -run it <imageid>
docker run -it <imageid> 'Hi Hari'
instead of Hi docker is replaced by Hi Hari.

## More about Docker
1. Applications era
2. Virtualization revolution
3. Problems with hiper visor architecture
4. Containers
5. Dockers
6. Installing docker

### Install docker on linux and verification few basic examples revisit

on web goto docker mauals
docker for linux

Install docker
$sudo yum -y update
$sudo yum install -y docker
$docker
$docker --version
$docker info
$sudo service docker start 
$docker info 
$clear
$add the user to docker 
$sudo usermod -a -G docker ec2-user
(no need to run sudo with every docker command)

$docker images
it will list all images
$docker ps
$docker ps -a
$docker ps -aq
$docker run hello-world
it will get this image from online docker hub

$clear
$docker images
$docker ps
$docker ps -a
$sudo service docker stop
$unistall docker
$sudo yum remove docker
$docker
https://get.docker.com

### How to install docker on windows?
ans:https://www.youtube.com/watch?v=HqBMEmoAd1M&list=PLhW3qG5bs-L99pQsZ74f-LC-tOEsBp2rK&index=8

### summary:
### Basic commands
docker version
docker -v
docker info
docker --help
docker login

### Image commands
docker images
docker pull
docker rmi

### Containers commands
docker ps
docker run
docker start
docker stop

### System commands
docker stats
docker system df
docker system prune


Basic commands:
docker version
docker -v
docker --version
docker info 
 gives detaild info 

docker --help 
  commands info
  docker images --help
  docker run  --help

docker login
  https://hub.docker.com
  is repo for images
  pull or push the images.

reduce the length of cmd prompt in mac
terminal $export PS1="\u$ "

Images commands:
$docker images
to see all the images

$docker pull ubuntu
 it will download the image from repo

$docker images

$docker images -q
only id

$docker images -a
full info

$docker images -aq

$docker rmi --help

$docker rmi imageid (to delete the images)

$docker rmi -f imageid

$docker images

$docker ps  --help
is used to list the running containers.

$docker ps 
will show you all running containers

$docker run ubuntu
unable to find image locally so it will pull 

$docker ps
still ubuntu is not running

$docker run -it ubuntu
i install
t goto ubuntu
#ls
# now docker command will not work
goto new terminal

$docker ps

$docker start containerid
$docker stop containerid

$docker stats

$docker run -it ubuntu
$docker stats

$docker system df
$docker system prune --help
$docker system prune
 be carefull about this command

 $docker stop <ubuntucontainerid>
 $docker ps 
 $docker ps -a
 $docker images
 $docker system prune -a
 Y
 $docker images

###  What are Docker Images | How to create Docker Images
 https://www.youtube.com/watch?v=QBOcKdh-fwQ&list=PLhW3qG5bs-L99pQsZ74f-LC-tOEsBp2rK&index=9

 1.What are images
 2.How to pull image
 3.How to run a container using an image
 4. Basic commands

###  What are images:
 ans: Docker images are templates used to create docker containers
 Container is a running instance of image

###  Where are images stored?
 Registries (eg docker hub)
 Images can be stored at local or remote locations

 $docker pull <image name:tag>
 tag is used to pull a speicif version of image

 $docker pull ubuntu:18.04
 $docker images --help
$docker pull image
$docker images 
$docker images -q
$docker images -f "dangling=false"
$docker images -f "dangling=false" -q
A dangling image is one that is not tagged and is not reference by an container.
$docker images -f "dangling=true" -q

$docker run imagename/imageid
$docker rmi imagename/imageid
$docker ps -a
$docker rimi -f image
$docker inspect
run the docker with aname
$docker run --name MyUbuntu1 -it ubuntu bash

### we can inspect the image
$docker inspect ubuntu
$docker images
$docker rmi ubuntu:18.04
$docker stop MyUbuntu1
$docker rmi ubuntu:18.04
now i can remove the image
but still it is not.

### How to remove the container and  How to remove the image

$docker container rm <containerid>
$docker rmi ubunutu:18.04
note: Docker can build images automatically by reading the instructions from a docker file
Containers are running instances of Docker images.
A single image can be used to create multiple containers.
For reference see below link:
https://linuxize.com/post/how-to-remove-docker-images-containers-volumes-and-networks/

### What are Docker Containers | How to create Docker Containers
$docker run hello-world
it will try to find the hello-world image locally.
If not found then it will try to get it from docker repo and creates a container.

$docker ps 
will list running containers.

$docker ps -a 
will list all containers.

$docker run --name myubuntu container1 -it ubuntu
it will get the latest

$docker start containerName/ID
$docker exec -it <container name> /bin/bash
$docker stop containerName/ID

$docker pause containerName/ID
$docker unpause containerName/ID

$docker top containerName/ID
$docker stats containerName/ID


$docker start cosntainerName/ID
$docker attach containerName/ID
$docker stop containerName/ID

$docker kill containerName/ID

$docker rm ContainerName/ID
$docker ps 

$docker historyImageName/ID


Use docker ps to get the name of the existing container.
Use the command docker exec -it <container name> /bin/bash to get a bash shell in the container.
Generically, use docker exec -it <container name> <command> to execute whatever command you specify in the containe
 $docker exec -it <container name> /bin/bash

###  What are containers?
 ans:
 Containers are running instances of docker images.
 A container image is a lightweight, stand-alone, executable package of a piece of software that includes everything needed to run it: code, runtime, system tools, system libraries, settings

### What are the  Features of containers:
 1.Lightweight
 2.Less resources are used
 3.Booting of containers is very fast
 4.can start, stop, kill remove containers easily and quickly
 5.Operating System resources can be shared within Docker
 6.Containers run on the same machine sharing the same operating system kernel. this makes it faster

 You can use command 
 $docker container create 
 to create container in stopped state.

https://www.youtube.com/watch?v=iN3he0eVUyw&list=PLhW3qG5bs-L99pQsZ74f-LC-tOEsBp2rK&index=11
### How to run Jenkins on Docker
 Step by step for beginers
 1. How to start Jenkisn on docker container
 2. Start and Stop Jenkins Container
 3. How to set Jenkins home on Docker Volume and Host Machine

 $docker pull jenkins
 $docker run -p 8988:8080 -p 50000:50000 jenkins

 $docker run --name MyJenkins -p 8080:8080 -p 50000:50000 -v /home/venkatas/Desktop/Jenkins_Home:/var/jenkins_home jenkins


### What is dockerfile | How to create and build docker file

1.What is Docker file
2.How to create Dockerfile
3.How to build image from Dockerfile
4.BasicCommands

Dockerfile is a text filw with instructions to build images automation of Docker Image creation

FROM
RUN
CMD

step1: create a file named Dockerfile
first line we use 
FROM scratch
FROM ubuntu 
ie some source image

Difference between RUN and CMD 
RUN is executed during the building of the image
CMD is executed only when you create a container out of the image.


content of the file
# getting base image ubuntu
FROM ubuntu
MAINTAINER  satya <satyanarayana.pramati@gmail.com>

RUN apt-get update

CMD ["echo", "Hello World...! from my first docker image"]

:wq!

cat Dockerfile

### How to build the image?
ans: $docker build location of the file
or if file is in currrent directory  
$docker build .

$docker build -t myimage1:1.0 .

$docker images

$docker run imageid

### What is Docker Compose | How to create docker compose file | How to use Compose

1. What | Why - Docker Compose

2. How to install

3.How to create docker compose file

4.How to use docker compose file to create services

5.Basic commands

TIPS

### What is docker compose
1) tool for defining & running multi-container docker applications
2) use yaml files to configure application services (docker-compse.yml)
3)can start all services with a single command: docker compose up
4)can stop all services with a single command: docker compse down
5) can scale up selected services when required


Step1: Install Docker compose
  2 ways:
  1.https://github.com/docker/compose/releases
  2.Using PIP
    pip install -U dokcer-compose

 step2: create docker compose file at any location on your system 
 docker-compose.yml
 sudo apt install docker-compose

 $mkdir dockerComposeEx
 $cd dockerCompseEx
 $vi docker-compose.yml
 version: '3'

 services:
    web:
      image: nginx
      ports:
      - 9090:80

    database:
      image: redis

 save and exit.
 $cat docker-compose.yml
 step3: check the validity of file by command
 $docker-compose config

Step4: Run docker-compose.yml file by a command
$docker-compose up -d 
$docker ps
you will see running containers

open browser then type
http://localhost:9090

$docker-compose down
$docker ps
you will see no containers running

step5: bring down application by coammand
$docker-compse down

How to scale?
--scale flag is used
see the help for scale

$docker-compse --help

$docker up -d --scale database=4
$docker ps
you will see single web
4 databases

$docker-compose down
$docker ps

### Docker volumes
### What is Docker Volume | How to create Volumes | What is Bind Mount | Docker Storage

1.What are volumes
2.How to create / list / delete valumes
3.How to attach volume to a container
4.How to share volume among containers
5.what are bind mounts

Volumes are the preferred mechanism for persisting data generated by and used by Docker containers

$docker volume //get information
$docker volume create
$docker volume Is
$docker volume inspect
$docker volume rm
$docker volume prune

### Use of volumes
Decoupling container from storage
Share volume (storage/data) among different containers
Attach volume to container
On deleting container volume does not delete

$docker info
$clear
$docker -v 
$clear
$docker volume --help

$docker volume create myvol1
$Docker volume ls
$docker volume inspect myvol1
$docker volume prune
$docker volume ls
### How can we use the volume
$docker pull jenkins
start the container
$docker run --name myjenkins1 -v myvol1:/var/jenkins_home -p 8989:8989 -p 50000:50000 jenkins
copy the password
http://localhost:8989
give the password
$docker run --name myjenkins2 -v myvol1:/var/jenkins_home -p 8999:8989 -p 50009:50000 jenkins

http://localhost:8999
give the same password

as volume is shared between two jenkins

### Bind Mount: a file or directory on the host machine is mounted into a container
we can use the physical location instead of the volume.
Create a 'jenkins' user on the host, note it's uid
docker run -u <jenkins-uid> ...
The below is not working we need to find alternative

$docker run --name myjenkins3 -v /home/venkatas/Desktop/Jenkins_Home/:/var/jenkins_home -p 8998:8989 -p 50008:50000 jenkins

### summary
By default all files created inside a container are stored on a writable container layer

The data does n't persist when that container is no longer running

A container's wrtable layer is rightly copuled to the host machine where the container is running. You can't easily move the data somewhere else.

Docker has tow options for containers to store files in the host machine so that the files are persisted even after the container stops.

### Volumes and BIND mounts
Volues are stored in a part of the host file system wich is managed by docker
Non-Docker processes should not modify this part of the filesystem

Bind mounts may be stored anywhere on the host system

Non-Docker processes on the Docker host or a Docker container can modify them at any time.

In Bind Mounts, the file or directory is refernece by its full path on the host machine.

Volumes are the best way to persist data in Docker.

Volumes are manage by docker and are isloated from the core functionality of the host machine.

A given volume can be mounted into multiple containers simultaneously.

When no running container is using a volume. the volume is still available to docker and is not removed automatically. You can remove unused volumes using docker volume prune.

When you mount a volume, it may be named or anonymous.

Anonymous volumes are not given an explicit name when they are firest mounted into a container.

Volumes also support the use of volume direvers. which allow you to store your data on remote hosts or cloud providers. among other possibilites.

Docker was created by Solomon Hykes
initially released - 13 march 2013

Solomon Hykes started Docker in France as internal project within dotCloud. a platform-as-a-service company

The software debuted to the public in Santa Clara at PayCon in 2013

Docker was released as open source in March 2013

Docker library is written in the Go Programming language.

### Docker Swarm| Step by Step | What is Docker Swarm | How to create Docker Swarm
1.What is Docker swarm
2.Why to use it
3.How to create a manage Docker swarm
4.Create service on docker swarm
5.Scaling services up and down
6.Features / Helpful Tips

A swarm is a group of machines that are running docker and joined into a cluster.
from source:
https://www.youtube.com/watch?v=bU2NNFJ-UXA&list=PLhW3qG5bs-L99pQsZ74f-LC-tOEsBp2rK&index=15

Docker swarm is a tool for container orchestration.

Let's take an example

You need to do
 - Health check on every container
 - Ensure of containers are up on every system
 - Scaling the containers up or down depending on the load
 - Adding updates/ changes to all the containers

 Orchestation- Managing and controlling multiple docker containers as a singl service 
 Tools availabe - Docker swarm, Kubernetes, Apache Mesos

### From source: Tech primers

 create a spring boot application
 in application.properties
 server.port=8089
 create the docker file as shown below:
 --------------------------
 DockerFile
 FROM openjdk:8
 ADD  target/docker-spring-boot.jar docker-spring-boot.jar
 EXPOSE 8090 
 ENTRYPOINT ["java", "-jar", "docker-spring-boot.jar"]

 -----------------
 goto project directory where docker file is there

 $docker -v
 build an image
 $docker build -f Dockerfile -t docker-spring-boot .

 $docker images
 you will see docker-spring-boot image is created.

 $docker run -p 8085:8090 docker-spring-boot

 ### How to Run/Deploy Spring Boot & MySQL in Docker
 $docker images
 mysql
 openjdk
 docker

$docker pull docker

 $docker pull mysql
 $docker pull openjdk:8  
 $docker run --name mysql-standalone -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=test -e MYSQL_USER=sa -e MYSQL_PASSWORD=password -d mysql:5.6

 $docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci

 creates docker container with mysql

 $docker container ls

 create the docker file
 ----------------------
 Dockerfile
 FROM openjdk:8
 ADD target/BootResourceApp.jar BootResourceApp.jar 
 EXPOSE 8086
 ENTRYPOINT ["java", "-jar", "BootResourceApp.jar"]
save and exit.

Now create the image
---------------------
$docker build . -t boot-resource-app
$docker run -p 8086:8086 --name boot-resource-app --link mysql-standalone:mysql -d boot-resource-app


$docker build . -t boot-resource-app2
$docker run -p 8089:8086 --name boot-resource-app2 --link mysql-standalone:mysql -d boot-resource-app2


$docker build . -t users-mysql
$docker run -p 8086:8086 --name users-mysql --link mysql-standalone:mysql -d users-mysql

$docker container ls

$docker logs users-mysql
$docker logs 

[{"rId":23,"rName":"satya","rRole":"LeadArchi","rSkillSet":"java","rSalary":5000.0},{"rId":25,"rName":"raju","rRole":"LeadTech","rSkillSet":"phython","rSalary":5000.0},{"rId":30,"rName":"usha","rRole":"QA","rSkillSet":"junit","rSalary":1000.0}]


Working on multi stage docker files.
