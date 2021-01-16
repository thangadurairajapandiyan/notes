# Docker Image
Contains app binaries and dependencies. Not a complete OS. No kernel, kernal mosules(eg, drivers). Small as one file, or big as a ubuntu distro with apt, and apache, php and more installed

### Notes
* Each layer in the docker image will have a unique sha256 value
* A container is just a single read/write layer on top pf image
* Multiple tags can point to the same imageid since the image is same
* If we are not specifing the CMD in the Dockerfile, it will use the CMD defined in the base docker image, this is working since everything will be inherited from the BASE dockerfile

### To know the layers of docker image
docker history nginx **or** docker image history nginx

### To see metadata of the docker image
docker inspect nginx **or** docker image inspect nginx

