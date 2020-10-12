

Installing Docker gives you the client and daemon
docker hub

Container and Images
Images ~ Stopped containers
Containers ~ Running images

Commands
docker run: to run a new container
docker ps: see running and stopped containers
docker images: list images stored locally

docker pull <repository>  pull from docker hub to local repository
Example
    docker pull ubuntu 
    docker pull ubuntu:14.04

docker rmi <repository>:<tag>


docker run -d <image>

-d detached
-it interactive
docker run -d -it <image>

docker stop : stops the running containers
docker rm : removes(deletes) stopped containers