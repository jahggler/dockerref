# Docker reference

**boot2docker ip**  
Display the docker IP address (useful when a pack is built with docker-compose)

**docker rm -f $(docker ps -q -a)**  
Delete all docker containers

**docker rmi -f $(docker images -q)**  
Delete all docker images


## Change the docker virtual machine size

If you don't have the **~/.boot2docker/profile** file yet,  
**boot2docker config > ~/.boot2docker/profile**

Then, in the new **~/.boot2docker/profile** file, change the size  
**DiskSize = 50000**

**boot2docker poweroff**  
**boot2docker destroy**  
**boot2docker init**  
**boot2docker up**

