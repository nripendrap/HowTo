

Installing Docker gives you the client and daemon
docker hub

Docker Hub: hosted repository service provided by docker for finding and sharing container images with your team.

Container and Images
Images ~ Stopped containers
Containers ~ Running images

Commands
docker run: to run a new container
docker ps: see running and stopped containers
docker images: list images stored locally

docker pull <repository>  pull docker image from docker hub to local repository
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




Run PostgreSQL on docker locally
---------------------------

docker pull postgres
docker images - list images stored locally

$  mkdir ${HOME}/postgres-data
$  docker run -d --name dev-postgres -e POSTGRES_PASSWORD=password -v C:/Users/PradNrip/postgres-data/:/var/lib/postgresql/data -p 5432:5432 postgres
$  docker ps

$  docker exec -it dev-postgres bash

root@4cfa88c05532:/# psql -h localhost -U postgres
psql (13.1 (Debian 13.1-1.pgdg100+1))
Type "help" for help.

postgres=# \l
                                 List of databases
   Name    |  Owner   | Encoding |  Collate   |   Ctype    |   Access privileges
-----------+----------+----------+------------+------------+-----------------------
 postgres  | postgres | UTF8     | en_US.utf8 | en_US.utf8 |
 template0 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
           |          |          |            |            | postgres=CTc/postgres
 template1 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
           |          |          |            |            | postgres=CTc/postgres
(3 rows)

$  dotnet publish -c Release -o site

Zip site directory
$ cd site
$ zip -r ../deploy_bundle.zip *
$ cd ..


Upload and deploy button

export ASPNETCORE_ENVIRONMENT="Production"
dotnet ef database update


Open Elastic Beanstalk dashboard
Click on environments
Click on Configuration -> Database
Click Edit 

docker pull redis
docker run -d --name dev-redis -p 6379:6379 redis






