# NOTE:
## Volumes can only be created
	1. while building the image (using Dockerfile)
	2. creating a container 
	- (--volumes-from and --privileged      option in docker run command)

# build the container from given Dockerfile.
	docker build -t myimage .

# Start and run the container.
	docker run -it -d --name mycentos myimage /bin/bash
	docker exec -it mycentos /bin/bash

# "VOLUME" mentioned in Dockerfile is actually defining a directory in the container as a volume 
## which can be shared from
	1. container to container
	2. container to host

# Now create some files on the VOLUME which is mentioned in Dockerfile. ( in our case "/root/public" )
	echo "Hello from centos" > /root/public/file1

## Create a new container of any distro choice with the following command
	docker run -it -d --name myubuntu --privileged=true --volumes-from mycentos ubuntu /bin/bash
	- --privileged=true ==> read/write full permission
	- --volumes-from ==> use volume of a container, here it is mycentos

# Now exec and verify the shared volume
	docker exec -it myubuntu /bin/bash
	INSIDE THE CONTAINER: 
		$ ls -l /root/
		$ cat /root/public/file1
		$ echo "Hello from ubuntu" >> /root/public/file1
		$ exit

# Verify the same on centos.

# NOTE:
## Volumes can only be created
	1. while building the image (using Dockerfile)
	2. creating a container 
	--volumes-from and --privileged option in docker run command)

## TRY TO CREATE VOLUME BY USING COMMAND
	docker run -it -d --name webserver1 -v /root/web_share centos /bin/bash

	docker exec -it webserver1 /bin/bash

## Create some files on VOLUME mentioned, in our case "/root/web-share"
	ls -ld /root/web_share

	echo "I AM WEB SERVER 1" > /root/web-share/index.html
	exit

## CREATE ONE MORE CONTAINER AND SHARE THE VOLUME
	docker run -it -d --name webserver2 --privileged=true --volumes-from webserver1 centos /bin/bash

## VERIFY THE SHARED VOLUME	
	docker exec -it webserver2 /bin/bash

	ls -ld /root/web_share
	echo "I AM WEBSERVER 2" >> /root/web_share/index.html
	exit
