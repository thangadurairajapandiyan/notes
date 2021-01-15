# Docker Image
Contains app binaries and dependencies. Not a complete OS. No kernel, kernal mosules(eg, drivers). Small as one file, or big as a ubuntu distro with apt, and apache, php and more installed

### Notes
* Each layer in the docker image will have a unique sha256 value

### To know the layers of docker image
docker history nginx **or** docker image history nginx

### To see metadata of the docker image
docker inspect nginx **or** docker image inspect nginx

