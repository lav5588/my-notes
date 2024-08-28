# Docker

### Docker Pull
        docker pull <image name>

It is used to pull a Docker image from the repository

### Docker images
        docker images

It is used to list the Docker images

### Docker ps
        docker ps 

It is used to list all the containers

#### Docker run
        docker run <image name>:<version>

It is used to run a Docker Image

        docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres

When a container is created there is a by default name assigned to the container. If we want to change the name of the container the we can pass the --name option with some-name.

When databases are run it needs some secret password so that anyone can't access the  database hence we pass -e option refers to the environment variable and we pass a key value pair to it.

-d is used to keep the terminal in detached mode it means terminal will not be busy . it will free. And we can use it.





