* Docker is a set of platform as a service (PaaS) products that use OS-level virtualization to deliver software in packages called containers.

* DevOps is a development methodology aimed at bridging the gap between Development and Operations, emphasizing communication and collaboration, continuous integration, quality assurance and delivery with automated deployment utilizing a set of development practices.
 So stripping the jargon we get two definitions:
		1. Docker is a set of tools to deliver software in containers.
		2. Containers are packages of software.

* "works on my machine" problem for the software that works in locale machine and doesn't on the server".
   List all your images with "docker image ls".

### Container
containers only contain that which is required to execute an application; and you can start, stop, and interact with them. They are isolated environments in the host machine with the ability to interact with each other and the host machine itself via defined methods (TCP/UDP).

* List all your containers with "docker container ls -a" or "docker ps".
* docker image rm hello-world.
  
Error response from daemon: conflict: unable to remove repository reference "hello-world" (must force) - container <container ID> is using its referenced image <image ID>

This means that a container that was created from the image hello-world still exists and that removing hello-world could have consequences. So before removing images, you should have the referencing container removed first. Forcing is usually a bad idea, especially as we are still learning.

> docker container rm command. It accepts a container's name or ID as its argument.

Notice that the command also works with the first few characters of an ID. For example, if a container's ID is 3d4bab29dd67, you can use docker container rm 3d to delete it. Using the shorthand for the ID will not delete multiple containers, so if you have two IDs starting with 3d, a warning will be printed, and neither will be deleted. You can also use multiple arguments: docker container rm id1 id2 id3

* If you have hundreds of stopped containers and you wish to delete them all, you should use: "docker container prune".

Prune can also be used to remove "dangling" images with "docker image prune". Dangling images are images that do not have a name and are not used. They can be created manually and are automatically generated during the build. Removing them just saves some space.

* You can also use the image pull command to download images without running them: "docker image pull hello-world".

* Let's try starting a new container: "docker container run nginx" or "docker container run -d nginx" if the terminal freeze.

* We should first stop the container using "docker container stop 'image'", and then use "rm".
* We can use "docker container rm --force'iamge'".
```  
Most used commands:
command 			    explain 					shorthand
docker image ls			    Lists all images	 			docker images
docker image rm <image>		    Removes an image				docker rmi
docker image pull <image>	    Pulls image from a docker registry	   	docker pull
docker container ls -a		    Lists all containers			docker ps -a
docker container run <image>	    Runs a container from an image		docker run
docker container rm <container>	    Removes a container				docker rm
docker container stop <container>   Stops a container				docker stop
docker container exec <container>   Executes a command inside the container 	docker exec
```

```
$ docker run -it ubuntu
```
* -i (interactive), -t (tty), and -d (detached)

```
$ docker run -d -it --name looper ubuntu sh -c 'while true; do date; sleep 1; done'
```

* The first part, "docker run -d". Should be familiar by now, run container detached.

* Followed by "-it" is short for "-i" and "-t". Also familiar, -it allows you to interact with the container by using the command line.

* Because we ran the container with "--name 'looper'", we can now reference it easily.

* The image is ubuntu and what follows it is the command given to the container.

* And to check that it's running, run "docker container ls".

Let's follow -f the output of logs with:
```
$ docker logs -f looper
  Thu Mar  1 15:51:29 UTC 2023
  Thu Mar  1 15:51:30 UTC 2023
  Thu Mar  1 15:51:31 UTC 2023
```




















