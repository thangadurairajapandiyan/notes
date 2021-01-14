# Docker

### To exec inside the container with diffrent user
docker exec -ti --user user_name CONTAINER_ID bash

### To know the pid of the container
docker top container_name/id

### To know information about the container
docker inspect container_name/id

### To know the statistics like ram and cpu consumed by each container
docker stats
