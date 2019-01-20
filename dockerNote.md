# Docker cheatsheat

## images

#### search available images on web    
    docker search IMAGENAME

#### download image to local machine
    docker pull IMAGENAME:latest

#### run image (will try download if it can't find it in local machine )
    docker run IMAGENAME
    ex: docker run -d -p 22345:80 --name=myweb1 nginx:latest

#### show local images    
    docker images


#### build images from dockerfile
    docker build -t [userid/tagname] [dockerfilepath]

----

## containers

#### show containers 
    docker ps

#### remove all containers(danger)
    docker rm `docker ps -a -q`

#### stop and start container 
    docker stop ["id"|"name"]
    docker start ["id"|"name"]

----

## other
#### check info
    docker inspect ["id"|"name"]

#### check port
    docker port ["id"|"name"]

#### access container 
    docker exec -it [id|name] [params]
    ex: docker exec -it myweb1 /bin/bash

#### mount things inside container
    docker run -d -p [localPort]:[containerPort] --name=myweb1 -v [localPath]:[containerPath] nginx:latest