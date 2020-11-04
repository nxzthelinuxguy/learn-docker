# Docker Port Expose

## Container does not have a ip of itself
## Docker port expose is used to expose port of a running container
## This can be achieved in 2 ways
### EXPOSE
	EXPOSE command is used inside a Dockerfile
	It is used for internal communication between the containers and  the docker host.

### Publish (-p)
	-p option is used while creating / running a container.
	It is used to expose the ports of a running container globally.
	It is a powerful option and has higher priority than EXPOSE.
	
	Eg:
		docker run -td --name my-jenkins -p 80:80 jenkins
	
	## Check open ports of a docker container
		docker port web1

	## Check port of the local machine
		netstat -tnlp  (assuming net-tools is installed)

### Jenkins is now accessible via host ip and exposed port
	http://ip:8080

## Docker Attach VS Docker Exec

### Docker Exec (assume new terminal everytime)
	1. Creates a new process in the container environment
	2. It is specifically for running new things in a already started container, be it a shell or some other process

### Docker Attach (assume as console access)
	Just connects the standard io of main process inside the container to the corresponding standard io error of current terminal

## Difference between EXPOSE and PUBLISH (-p)

#### Basically you have three options:
		1. Neither specify EXPOSE nor PUBLISH (-p)
		2. Only specify EXPOSE
		3. Specify EXPOSE and PUBLISH (-p)

####	### If you specify neither EXPOSE nor PUBLISH (-p) , the service in the container will only
	    be accessible from inside the container itself

####	### If you EXPOSE a port, the service in the container will not be accessible from outside docker, 
	    but from inside docker containers 
	    EXPOSE is good for inter-container communication
