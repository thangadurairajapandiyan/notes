# Docker Network

### Notes
* We can attach more than one networks to container
* We can dynamically attach and remove the additional networks
* Container craeted with host network connect attach any othetr additional networks

### List networks available
docker network ls

### Inspect a network
docker network inspect

### Create a network
docker network create --driver bridge

### Attach a network to container
docker network connect

### Detach a network from container
docker network disconnect
