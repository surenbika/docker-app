# docker-app

This is a sample application to demonstrate some of the docker capabilities

# Pre-requisites

You must have Docker installed for this code to work! Check the [Installation Guide](https://docs.docker.com/engine/installation/) if you haven't got it installed.

# Coding

To start or stop the test database, build the test-database image and run it:

```bash
cd ./test-database
docker build -t test-database .
docker run --name db test-database 
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
docker-compose -d up

# To shutdown the containers gracefully
docker-compose -d down
```
