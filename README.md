# Docker Cheatsheet
@your_own_risk

LIST CONTAINERS
```
docker ps -l
```
CONNECT TO EXISTING CONTAINER INSTANCE
```
docker attach <CONTAINERID/NAME> #by ID
```

OPEN NEW BASH PROMPT ON RUNNING CONTAINER
```
docker exec -i -t <CONTAINERID/NAME> bash
```

FIND OUT CONTAINER ID BY USING 	
```
docker ps -l 
```

COMMIT CONTAINER TO MAKE IMAGE
```
docker commit <CONTAINER ID>
```

TAG THE IMAGE
```
docker tag <ImageName> RepoName:Tagdocker 
```

PULL IMAGE FROM REGISTRY
```
docker pull <REGISTRY>/<IMAGENAME>
```

PUSH IMAGE TO REGISTRY
```
docker push <REGISTRY>/<IMAGENAME>
```
SAVE IMAGE TO DISK
```
docker save -o <save image to path> <image name>
```

LOAD SAVED IMAGE FROM DISK
```
docker load -i <path to image tar file>
```

DELETE ALL UNTAGGED IMAGES
```
docker rmi $(docker images | grep "<none>" | awk '{print $3}')
sudo docker rmi $(sudo docker images | grep "<none>" | awk '{print $3}')
sudo docker stop $(sudo docker ps |  grep automodo | awk '{print $1}')
```

DELETE ALL IMAGES(LOCAL)
```
docker rmi $(docker images -q)
```

DELETE ALL CONTAINERS (LOCAL)
```
docker rm $(docker ps -a -q)
```

DELETE EXITED CONTAINERS
```
sudo docker ps -a | grep 'weeks ago' | awk '{print $1}' | xargs --no-run-if-empty sudo docker rm
sudo docker ps -a | grep 'days ago' | awk '{print $1}' | xargs --no-run-if-empty sudo docker rm
sudo docker ps -a | grep 'Exited' | awk '{print $1}' | xargs --no-run-if-empty sudo docker rm
sudo docker ps -a | grep 'Dead' | awk '{print $1}' | xargs --no-run-if-empty sudo docker rm
```

STOPPING ALL DEAD CONTAINERS
```
sudo docker ps -a | grep 'Dead' | awk '{print $1}' | xargs --no-run-if-empty sudo docker stop
sudo docker ps -a | awk '{print $1}' | xargs --no-run-if-empty sudo docker stop
```

GET DOCKER CONTAINER IP
```
docker inspect --format '{{ .NetworkSettings.IPAddress }}' <CONTAINER ID>
```
COPY FILES FROM DOCKER CONTAINER TO HOST (AND BACK)
```
docker cp <containerId>:/file/path/within/container /host/path/target
docker cp <containerId>:/file/path/within/container /host/path/target
```

### DOCKERFILE

WHEN DOCKERFILE IS IN CURRENT FOLDER
```
sudo docker build -t <TAG> .
```

