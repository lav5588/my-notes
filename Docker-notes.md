# Docker


        docker pull <image name>

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

### Docker run
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