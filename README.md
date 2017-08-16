# docker-app

This is a sample application to demonstrate some of the docker capabilities

# Pre-requisites

You must have Docker installed for this code to work! Check the [Installation Guide](https://docs.docker.com/engine/installation/) if you haven't got it installed.

# Coding

To start or stop the test database, build the test-database image and run it:

```bash
cd ./test-database
docker build -t test-database .
docker run -it -p 3306:3306 test-database
```

```bash
docker build -t users-service .
docker run -it -p 8123:8123 --link db:db -e DATABASE_HOST=DB users-service
```

At this moment, we should be able to access our db at http://localhost:8123/users 

# Install docker-compose
https://docs.docker.com/compose/install/#install-compose-on-mac-or-windows-systems


To test the entire stack, run:


```bash
# Build docker-compose
docker-compose build

# To Bring the stack up
docker-compose up

# To shutdown the containers gracefully
docker-compose down
```

# To scale up:
create 2 More VMs, install docker on them(VM2 and VM3)

#Install docker swarm on VM1
https://docs.docker.com/engine/swarm/swarm-tutorial/create-swarm/

#Create docker cluster

docker swarm init

join from other VMs, so that all 3 VMs are in a cluster

Create swarm service on swarm manager 

```bash
cd ./test-database
docker build -t test-database .
docker service create --name db -p 3306:3306 test-database 

# To scale up
docker service scale db=3 

# To verify docker cluster
docker service ls

and
docker service ps db
```
