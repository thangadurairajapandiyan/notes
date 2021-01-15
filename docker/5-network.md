# Docker Network

### Notes
* We can attach more than one networks to container
* We can dynamically attach and remove the additional networks
* Container created with host network connect attach any othetr additional networks
* If we remove the default bridge network from the container, container can still run without any network.
* Container with "none" network is different from container without any network
* containers in the same network can talk to each other using the container name. This is possible because of DNS resolution handled by docker
* Only With default bridge network, DNS resolution will not work(does not have dns server builtin), so that the containers cannot talk to each other, we have to use --link to link the containers we want to talk.
* DNS resolution perfectly works with the newly created network and the containers in that network can talk to each other with the container name without creating the link

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
