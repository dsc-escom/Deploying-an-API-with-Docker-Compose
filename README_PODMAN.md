
# Mongo API

## Create Network

~~~ BASH

podman network create --subnet 10.10.0.0/16 api-network

~~~ 

## Pull mongo image

~~~ BASH
podman image pull docker.io/mongo:5.0.14
~~~

## Create a container
~~~ BASH
podman container run -d \
    --name mongoDB \
    --ip=10.10.0.2 \
    --network=api-network \
    -e MONGO_INITDB_ROOT_USERNAME=mongoadmin \
    -e MONGO_INITDB_ROOT_PASSWORD=secret \
    mongo:5.0.14
~~~

## Build a container
~~~ BASH
podman build -t flask-rest Flask
~~~

## Create a API container

~~~ BASH

podman run -dt \
    --name api-flask \
    -p 5000:5000 \
    --ip=10.10.0.3 \
    --network=api-network \
    -e MONGO_INITDB_ROOT_USERNAME=mongoadmin \
    -e MONGO_INITDB_ROOT_PASSWORD=secret \
    -e MONGODB_HOST=10.10.0.2\
    flask-rest
~~~