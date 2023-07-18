# Docker Crash Course by Net Ninja
https://www.youtube.com/watch?v=ZVQmnziXEpA&list=PL4cUxeGkcC9hxjeEtdHFNYMtCpjNBm3h7


## Lesson 4. Node Image and Docker Hub
For those getting immediate exit "bug", please run this command:
> docker run -dit node:<node version>


## Lesson 5. the Dockerfile
https://docs.docker.com/engine/reference/builder/
https://docs.docker.com/language/nodejs/build-images/
Build a docker image
> docker build -t <image_name>:<tag_name> .
where . is a relative path to the Dockerfile

Example build a docker image from Dockerfile in current directory (.)
> docker build -t myapp:v1 .

Once an image is made, it is read-only.


## Lesson 6. .dockerignore file


## Lesson 7. Starting and Stopping Containers from Command Line
list all images
> docker images

create and run container from image
> docker run --name <container_name> <image_name>

create and run container from image and (-p) map port (-d) detach mode
> docker run --name <container_name> -p <port_number>:<container_port_number> -d --rm <image_name> 

(-d) detach mode runs without blocking terminal
(--rm) remove the container when we stop it

list all currently running containers
> docker ps

list all containers
> docker ps -a

stop container
> docker stop <container_name>

restart container in detached mode
> docker start <container_name>

restart container in interactive mode
> docker start -i <container_name>


## Lesson 8. Layer Caching

## Lesson 9. Managing images & containers

Remove an image
> docker image rm <image_name>

Force remove an image still in use
> docker image rm <image_name> -f

Remove an container
> docker container rm <container_name>

Remove all containers, images (not in use)
> docker system prune -a

Remove all volumes (not in use)
> docker volume prune -a


## Lesson 10. Volumes

Volumes: folders on host computer map to container on docker, local files mirrored automatically without re-building new images, useful for development.

Rebuild image (docker build) to share with others.

Add a script to package.json that runs nodemon:
"scripts": {
  "dev": "nodemon -L app.js"
}

`-L` or `--legacy-watch` flag  is needed changes how nodemon works on windows in containers
> nodemon -L app.js
https://github.com/remy/nodemon

create a container to pick up the volume
> docker run --name <container_name> -p <HOST_PORT>:<CONTAINER_PORT> --rm -v <local_absolute_path>:<container_path> -v <container_path> <image_name:<tag>

(-v <local_absolute_path>:<container_path>) creates volume mapping from local path to container path and keep them in sync
(-v <container_path>) creates anonymous volume not mapped to specific location on local computer, but mapped to a location managed by docker somewhere on the local computer, and the contents of that folder will persist even when the container stops

Example: /app/node_modules folder in the container mapped anonymously to somewhere on our computer to overwrite previous volume so it persists on the container even if the local node_modules folder is deleted.
> docker run --name myapp_c_nodemon -p 4001:4000 --rm -v /home/wei/docker/node/api:/app -v /app/node_modules myapp:nodemon

View all volumes
> docker volume ls


## Lesson 11. Docker Compose
https://docs.docker.com/compose/compose-file/03-compose-file/

Create images and containers
> docker-compose up
 
Create images and containers in detached mode
> docker-compose up -d

Stop and delete all containers created by docker-compose
> docker-compose down

Delete all images created by docker-compose
> docker-compose down --rmi all

Delete all images and volumes created by docker-compose
> docker-compose down --rmi all --volumes

Delete all volumes created by docker-compose
> docker-compose down --volumes


## Lesson 12. Dockerizing a React app
Go to https://hub.docker.com/ and create a repository.

> docker login
> docker push missweizhang/myapi
> docker pull missweizhang/myapi


## Reference
Dockerfile Reference
https://docs.docker.com/engine/reference/builder/

Docker Compsose Reference
https://docs.docker.com/compose/compose-file/
