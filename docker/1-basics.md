# Docker

### To know the configuration of docker daemon/sercre
docker info

### To exec inside the container with diffrent user
docker exec -ti --user user_name CONTAINER_ID bash

### To know the pid of the container
docker top container_name/id

### To know information about the container
docker inspect container_name/id

### To know the statistics like ram and cpu consumed by each container
docker stats

### To change the docker registry details for login from the host
Update the ~./docker/config.json
