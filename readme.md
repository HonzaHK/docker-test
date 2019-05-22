## running containers
- build and run `docker-compose.yml` configuration
```
docker-compose up --build -d
```


## initializing project
- connect to the webserver container and start bash
```
docker exec -it test_webserver_1 /bin/bash
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