# learning-docker
Learning Docker.

Just on of the things I'm learning. https://github.com/hchiam/learning

# Use Docker - Essential Commands For Me:

`docker images` shows you the images you have locally on your computer.

`docker search ...` shows you search results (for whatever's in "...") for docker images found on docker hub.

`docker pull ...` downloads a docker image (put a name in "..."). (Examples: `sudo docker pull bitnami/wordpress:latest` and `sudo docker pull mprasil/dokuwiki`)

`docker run ...` runs a docker image (put a name in "...").

`docker rmi ...` deletes a docker image (put a name in "...").

More info: https://www.howtoforge.com/tutorial/docker-how-to-use-it-in-a-practical-way-part-3/

# Use Docker - Get Started:

https://docs.docker.com/get-started/

Create Dockerfile, app.py, and requirements.txt.

`docker build -t friendlyhello .`

Check image in local Docker image registry: `docker images`

**Run the app**: `docker run -p 4000:80 friendlyhello`

http://localhost:4000

Quit in Terminal: CTRL+C

**To run the app in the background:**

`docker run -d -p 4000:80 friendlyhello`

`docker ps` to get the container ID

`docker stop <container-id>` to end the process

## part 2 cheatsheet:

```bash
docker build -t friendlyname .  # Create image using this directory's Dockerfile
docker run -p 4000:80 friendlyname  # Run "friendlyname" mapping port 4000 to 80
docker run -d -p 4000:80 friendlyname         # Same thing, but in detached mode
docker ps                                 # See a list of all running containers
docker stop <hash>                     # Gracefully stop the specified container
docker ps -a           # See a list of all containers, even the ones not running
docker kill <hash>                   # Force shutdown of the specified container
docker rm <hash>              # Remove the specified container from this machine
docker rm $(docker ps -a -q)           # Remove all containers from this machine
docker images -a                               # Show all images on this machine
docker rmi <imagename>            # Remove the specified image from this machine
docker rmi $(docker images -q)             # Remove all images from this machine
docker login             # Log in this CLI session using your Docker credentials
docker tag <image> username/repository:tag  # Tag <image> for upload to registry
docker push username/repository:tag            # Upload tagged image to registry
docker run username/repository:tag                   # Run image from a registry
```

## part 3 cheatsheet:

```bash
docker stack ls              # List all running applications on this Docker host
docker stack deploy -c <composefile> <appname>  # Run the specified Compose file
docker stack services <appname>       # List the services associated with an app
docker stack ps <appname>   # List the running containers associated with an app
docker stack rm <appname>                             # Tear down an application
```

## part 4 cheatsheet:

```bash
docker-machine create --driver virtualbox myvm1 # Create a VM (Mac, Win7, Linux)
docker-machine create -d hyperv --hyperv-virtual-switch "myswitch" myvm1 # Win10
docker-machine env myvm1                # View basic information about your node
docker-machine ssh myvm1 "docker node ls"         # List the nodes in your swarm
docker-machine ssh myvm1 "docker node inspect <node ID>"        # Inspect a node
docker-machine ssh myvm1 "docker swarm join-token -q worker"   # View join token
docker-machine ssh myvm1   # Open an SSH session with the VM; type "exit" to end
docker-machine ssh myvm2 "docker swarm leave"  # Make the worker leave the swarm
docker-machine ssh myvm1 "docker swarm leave -f" # Make master leave, kill swarm
docker-machine start myvm1            # Start a VM that is currently not running
docker-machine stop $(docker-machine ls -q)               # Stop all running VMs
docker-machine rm $(docker-machine ls -q) # Delete all VMs and their disk images
docker-machine scp docker-compose.yml myvm1:~     # Copy file to node's home dir
docker-machine ssh myvm1 "docker stack deploy -c <file> <app>"   # Deploy an app
```

# Extra Cheat Sheets:

https://www.docker.com/sites/default/files/Docker_CheatSheet_08.09.2016_0.pdf

https://github.com/wsargent/docker-cheat-sheet
