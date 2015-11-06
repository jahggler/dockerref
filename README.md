# Docker reference

```
docker ps
```
Display all running containers

```
docker ps -a
```
Display all created containers

```
boot2docker ip
```
Display the docker IP address (useful when a pack is built with docker-compose)

```
docker rm -f $(docker ps -q -a)
```
Delete all docker containers

```
docker rmi -f $(docker images -q)
```
Delete all docker images

```
docker ps
```
Show running containers

```
docker run --name mycontainer -l com.example.server=server1 myimagename
```
Run **myimagename** in a container named **mycontainer** and set the label **com.example.server** value to **server1**

```
docker ps --format="{{.Image}}" --filter="label=com.example.server=server1"
```
Get image name based on the label value

```
docker ps --format="{{.Names}}" --filter="label=com.example.server=server1"
```
Get container name based on the label value

## Change the docker virtual machine size

If you don't have the **~/.boot2docker/profile** file yet,  
```
boot2docker config > ~/.boot2docker/profile
```

Then, in the new **~/.boot2docker/profile** file, change the size  

```
DiskSize = 50000
```

Then reinstall boot2docker

```
boot2docker poweroff
boot2docker destroy
boot2docker init
boot2docker up
```

## Docker IP Address

```
docker inspect --format='{{.NetworkSettings.IPAddress}}' CONTAINER_NAME
```

## Route to Docker

```
sudo route -n add 172.17.0.0/16 `boot2docker ip`
```

## SSH access to docker

```
docker exec -it CONTAINER_ID bash
```

## SSH access to boot2docker

```
boot2docker ssh
```

## An error occurred trying to connect: Get https://xx:xx/v1.20/containers/json: x509: certificate is valid for 127.0.0.1, xx, xxx, not xxxx 

First, try ```boot2docker upgrade``` because there was a known bug before 1.7.1.

Then, finally, if it doesn't work, disable all certificate checks

```
alias docker="docker --tlsverify=false"
```
