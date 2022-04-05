# Dockerfile
A `Dockerfile` is a text document that contains all the commands a user could call on the command line to assemble an image.

## Dockerfile Instructions
```docker
FROM        node:alpine
LABEL       author="Manh Tan"
ENV         NODE_ENV=production
WORKDIR     /var/www
COPY        . .
RUN         npm install
EXPOSE      3000
ENTRYPOINT  ["node", "server.js"]
```
## Building a Custom Image
```bash
docker build -t <name> .

# Using Registry Name, Image Name and Tag
docker build -t <registry>/<name>:<tag>
```

## Deploy an Image to Docker Hub
```bash
docker push <user_name>/<image_name>:<tag>
```
## Running a Container
```bash
docker run -p <externalPort>:<internalPort> <imageName>
```

## Images, Containers and File Layers

## Using docker logs to view 
```bash
docker logs <container_id>

```

## Creating a Container Volumn
```bash
docker run -p <ports> -v $(pwd)/var/www/logs <imageToRun>
```

## Key docker network Commands
```bash
docker network create
docker network ls
docker network rm [network]

# Running a database container in a network
docker run -d --net=isolated_network --name=mongodb mongo

docker run -d -p 3000:3000 -net=isolated_network --name=nodeapp imageName
```

## Using docker exec to Shell into a container
```bash
docker exec -it <containerId> sh
```

# Docker Compose Features
* Start, stop and rebuild services
* View the status of running services
* Stream the log output of running services
* Run a one-off command on a service

## Using Docker Compose Commands
```bash
docker-compose build
docker-compose up
docker-compose down
```

## YAML Fundamentals
* YAML files are composed of maps and lists
* Identation matters
* Alway use spaces
* Maps:
    * name: value pars
    * Map can contains other maps for more complex data structures
* Lists:
    * Sequence of items
    * Multiple maps can be defined in a list

## Key Service Configuration Options
* build
* environment
* image
* networks
* ports
* volumes