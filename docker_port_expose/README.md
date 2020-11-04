# Docker Port Expose
#### Container does not have a ip of itself
#### Docker port expose is used to expose port of a running container

### THIS COULD BE ACHIEVED IN 2 WAYS

##### EXPOSE
	1. EXPOSE command is used inside a Dockerfile
	2. It is used for internal communication between the containers and  the docker host.

##### Publish (-p)
	-p option is used while creating / running a container.
	It is used to expose the ports of a running container globally.
	It is a powerful option and has higher priority than EXPOSE.
	
	Eg:
		docker run -td --name my-jenkins -p 80:80 jenkins
	
	<h3> Check open ports of a docker container </h3>
		# docker port web1

	<h3> Check port of the local machine </h3>
		# netstat -tnlp  (assuming net-tools is installed)

##### Jenkins is now accessible via host ip and exposed port
	http://machine-ip:8080

### Docker Attach VS Docker Exec

##### Docker Exec (assume new terminal everytime)
	1. Creates a new process in the container environment
	2. It is specifically for running new things in a already started container, be it a shell or some other process

##### Docker Attach (assume as console access)
	Just connects:
	 THE standard i/o of main process inside the container
	 TO the corresponding standard i/o error of current terminal

### Difference between EXPOSE and PUBLISH (-p)

##### Basically you have three options:
		1. Neither specify EXPOSE nor PUBLISH (-p)
		2. Only specify EXPOSE
		3. Specify EXPOSE and PUBLISH (-p)

#### If you specify neither EXPOSE nor PUBLISH (-p) 
	 the service in the container will only be accessible from inside the container itself.

#### If you EXPOSE a port
	 the service in the container 
		will not be accessible from outside docker host
	 	but is accessible to inside docker containers. 
<h4>EXPOSE is good for inter-container communication. </h4>
