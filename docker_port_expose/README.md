# Docker Port Expose

## Container does not have a ip of itself
## Docker port expose is used to expose port of a running container
## This can be achieved in 2 ways
### EXPOSE
	EXPOSE command is used in a Dockerfile
	It is used for internal communication between the containers and  the docker host.

### -p
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
