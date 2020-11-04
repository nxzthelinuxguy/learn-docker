# Docker Port Expose
#### 1. Container does not have a ip of itself
#### 2. Docker port expose is used to expose port of a running container

### THIS COULD BE ACHIEVED IN 2 WAYS

##### EXPOSE
	- EXPOSE command is used inside a Dockerfile
	
	- It is used for internal communication between the containers and  the docker host.

##### PUBLISH
	- -p option is used while creating / running a container.

	- It is used to expose the ports of a running container globally.

	- It is a powerful option and has higher priority than EXPOSE.
	
###### Example
	docker run -td --name my-jenkins -p 80:80 jenkins
	
###### Check open ports of a docker container
	docker port web1

###### Check open port in the local machine
	netstat -tnlp  
	(assuming net-tools is installed)

###### Jenkins is now accessible via host ip and exposed port
	http://machine-ip:8080

### Docker Attach VS Docker Exec

#### Docker Exec 
##### assume DOCKER EXEC as
##### opening a new gnome terminal
##### opening ssh connections, etc. 
	
	- It creates a new process in the container environment
	
	- It is specifically for running new things in a already started container, be it a shell or some other process

#### Docker Attach (assume as console access)
##### Just connects:
	THE standard i/o of main process inside the container TO the 
	corresponding standard i/o error of current terminal

### Difference between EXPOSE and PUBLISH (-p)

#### Basically you have three options:
		1) Neither specify EXPOSE nor PUBLISH (-p)
		2) Only specify EXPOSE
		3) Specify EXPOSE and PUBLISH (-p)

#### If you specify neither EXPOSE nor PUBLISH (-p) 
###### SERVICE INSIDE THE CONTAINER
		- ONLY accessible from inside the container itself.

#### If you EXPOSE a port
###### SERVICE INSIDE THE CONTAINER
		- NOT accessible FROM OUTSIDE docker host
	 	- but accessible to INSIDE docker containers and host. 
<h4>EXPOSE is good for inter-container communication. </h4>

#### If you EXPOSE and PUBLISH a port
###### SERVICE INSIDE THE CONTAINER
		- Accesible from anywhere
		- even outside docker

#### IF YOU DO '-p' but do not expose
######		The docker does an implicit expose.
######		This is because, the port is open to the public, so it is also open for local containers.
