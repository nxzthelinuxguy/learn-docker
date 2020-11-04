# DOCKER DAY 1 
	Docker is built by integrating multiple different components
	This is known as DOCKER ECOSYSTEM
	Docker containers are layered file systems

# Container Creation 
## 3 ways:
	1. pull the container from dockerhub
	2. use Dockerfile
	3. build container from existing container / image

# Docker Basics

## SEARCH DOCKER IMAGES
	docker search image-name

## PULL / DOWNLOAD DOCKER IMAGES
	docker pull image-name

## LIST DOWNLOADED IMAGES
	docker images

## CREATE A CONTAINER 
	docker run -it -d --name container-name image-name /bin/bash
		- i: interactive
   	  	- t: TTY
   	  	- d: run as a daemon
   	  	- --name: NAME OF CONTAINER

## START A CONTAINER
	docker start container-name

## STOP A CONTAINER
	docker stop container-name

## TO GO INSIDE THE CONTAINER
	docker attach container-name  --> it will stop the container once exit 

## IF YOU WANT TO LEAVE WITHOUT STOPPING CONTAINER
	docker exec -it container-name /bin/bash  
	--> container will run even after exit

## TO SEE ALL THE CONTAINERS
	docker ps -a

## TO SEE ONLY RUNNING CONTAINERS
	docker ps

## TO DELETE A CONTAINER
	docker rm container-name 

## TO DELETE A IMAGE
	docker rmi  image-name

# Dockerfile 

##Dockerfile is a text document which contains some set of instructions.

## Using Dockerfile:	

	1. We can create our own custom image with a desired state

	2. Automation of docker image creation

## COMPONENTS:

	- FROM:
		For base image.

	- RUN:
		Execute commands, it will create layers in image.

	- MAINTAINER:
		Author/Owner

	- COPY:
		Copy file from local FS. Need to mention source and destination
		Can't download file from the internet
	
	- ADD:
		Timilar to copy, but also provides a feature to download files from the internet
		Also extracts zip, tar files

	- EXPOSE:
		To expose ports eg: 80 for apache, 8080 for tomcat
 
	- WORKDIR:
		To set working directory for a container

	- CMD:
		Executes commands but during container creation
		Ends after the end of container creation.

	- ENTRYPOINT:
		Similar to CMD, but has higher priority over CMD.
		First commands will be executed by ENTRYPOINT only

	- ENV:
		Environment Variables 
		Exist inside container 

	- ARGS
		Build time variables
		Destroyed once container is built
	
	- VOLUME: 
		Mention a volume
		eg: ["/public"]
