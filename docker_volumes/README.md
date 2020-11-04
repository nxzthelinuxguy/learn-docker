1. build the container from given Dockerfile.
	# docker build -t myimage .

2. Start and run the container.
	# docker run -it -d --name mycentos myimage /bin/bash

3. "VOLUME" mentioned in Dockerfile is actually defining a directory as a volume 
    which can be shared from
	- container to container
	- container to host

4. Now create some files on the VOLUME which is mentioned in Dockerfile. (in our case /root/public)
	# echo "Hello from centos" > /root/public/file1

5. Create a new container of any distro choice with the following command
	# docker run -it -d --name myubuntu --privileged=true --volumes-from mycentos ubuntu /bin/bash

6. Now exec and verify the shared volume
	# docker exec -it myubuntu /bin/bash
	
	$ ls -l /root/
	$ cat /root/public/file1
	$ echo "Hello from ubuntu" >> /root/public/file1
	$ exit

7. Verify the same on centos.

- NOTE:
	1. Volumes can only be created
		- while building the image (using Dockerfile)
		- creating a container (--volumes-from and --privileged      option in docker run command)

 
