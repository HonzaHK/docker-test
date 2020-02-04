## running containers
- build and run `docker-compose.yml` configuration
```
docker-compose up --build -d
```


## initializing project
- connect to the webserver container and start bash
```
docker exec -it YOUR_CONTAINER_NAME /bin/bash
```
- disconnect from container (it will exit bash process)
```
CTRL + d
```

- inside container, switch to user created via Dockerfile
```
su hk
```

- go to directory with project
```
cd /var/www/html/neziskovky
```

- run initialization scripts
```
./bin/install.js
```

## removing images/containers
  - images: `docker rmi -f $(docker image ls -q)`
  - containers: `docker rm -f $(docker container ls -a -q)`
  - networks: `docker network rm $(docker network ls -q)`
  - all: `docker rm -f $(docker container ls -a -q); docker rmi -f $(docker image ls -q); docker network rm $(docker network ls -q)`

## check docker-compose.yml with .env variables filled

```
docker-compose config
```
