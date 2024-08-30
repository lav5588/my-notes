# Docker


        docker pull <image name>:<version>

`docker pull` is used to pull a Docker image from the repository

        docker images

`docker images` is used to list the Docker images.

        docker image ls
`docker image ls` is used to list the Docker images.

        docker ps 

`docker ps` is used to list all the running containers

        docker container ls
`docker container ls` also used to list all the Docker running containers

        docker container ls -a

`docker container ls -a` is used to list all the Docker whether it is running or not

        docker run <image name>:<version>

`docker run` is used to run a Docker Image

        docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres

When a container is created there is a by default name assigned to the container. If we want to change the name of the container the we can pass the `--name` option with `some-name`.

When databases are run it needs some secret password so that anyone can't access the  database hence we pass `-e` option refers to the `environment variable` and we pass a `key=value` pair to it.

`-d` is used to keep the terminal in `detached mode` it means terminal will not be busy . it will free. And we can use it.



        docker stop <options> <container name or id>

`docker stop` is used to stop a running container.

        docker container stop <options> <container name or id>
`docker container stop` is alos used to stop a running container.


        docker container prune


The `docker container prune command` is specifically designed to remove all stopped containers from your Docker environment. It does not remove running containers. It can be `useful` as well as `dangerous` also.

        docker volume ls
`docker volume ls` is used to list all the volumes.

        docker pull mongo
`docker pull mongo` is used to pull the latest version of MongoDB image.

        docker run --name mongo-one  -p 4000:27017 -d mongo
`-p 4000:27017` is expose the port of MongoDB to the local machine

        docker logs <container name or id>
`docker logs` is used to log information of a running container.

        docker network create <network name>

`docker network create` is used to create to create a network.



        docker run --name mongo-two -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --net mongo-network -d mongo
`--net`  is used to provide a network to mongodb on which we it will run. here we pass name of the network in this case we pass `mongo-network`.

        docker network ls <options>
`docker network ls` is used to list the network.

        docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password -e ME_CONFIG_MONGODB_SERVER=mongo-two --net mongo-network --name mongo-express mongo-express
It pull and run the `mongo-express` image on the given network and given mongo container instance. And we can access it web base GUI on port `8081`.





## Docker Compose
Docker Compose is a tool for defining and running multi-container applications. It is the key to unlocking a streamlined and efficient development and deployment experience.

Compose simplifies the control of your entire application stack, making it easy to manage services, networks, and volumes in a single, comprehensible YAML configuration file. Then, with a single command, you create and start all the services from your configuration file.

Compose works in all environments; production, staging, development, testing, as well as CI workflows. It also has commands for managing the whole lifecycle of your application:

- Start, stop, and rebuild services
- View the status of running services
- Stream the log output of running services
- Run a one-off command on a service


```yaml
//Docker-compose.yaml
version: '3'
services:
  mongodb:
    image: mongo
    ports:
      - "27017:27017"
    environment:
      - MONGO_INITDB_ROOT_USERNAME=admin
      - MONGO_INITDB_ROOT_PASSWORD=password
    volumes:
      - mongo-data:/data/db

  mongo-express:
    image: mongo-express
    restart: always
    ports:
      - "8081:8081"
    environment:
      - ME_CONFIG_MONGODB_ADMINUSERNAME=admin
      - ME_CONFIG_MONGODB_ADMINPASSWORD=password
      - ME_CONFIG_MONGODB_SERVER=mongodb

volumes:
  mongo-data:
    driver: local
```

        docker-compose -f <filePath> up
`docker-compose -f <filePath> up` is used to run the `yaml` file.

        docker-compose -f <filePath> down
`docker-compose -f <filePath> down` iis used to stop and remove all containers, networks, and other resources that were created by `docker-compose up` for the services defined in a `docker-compose.yml` file.



## Dockerfile
Docker can build images automatically by reading the instructions from a Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. This page describes the commands you can use in a Dockerfile.


### Deploying a python project on dockerhub 

```python
//index.py
from flask import flask
helloworld = Flask(__name__)
@helloworld.route("/")
def run():
    return "{\"message\":\" Hey there python\"}"

if __name__ == "__main__":
    helloworld.run(host="0.0.0.0", port= int("3000"),debug=True)
```

```txt
//requirements.txt
flask
```

```Dockerfile
//Dockerfile
FROM python:3-alpine3.15
WORKDIR /app
COPY . /app
RUN pip install -r requirements.txt
EXPOSE 3000
CMD python ./inex.py
```
         docker build -t lav5588/hey-python-flask:0.0.0.1.RELEASE .
` docker build -t lav5588/hey-python-flask:0.0.0.1.RELEASE .`  is used to build a Docker image from the contents of the current directory (`.`), which usually contains a       `Dockerfile` and other necessary files.
