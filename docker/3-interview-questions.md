# Docker

### How to pass a dockerfile which is in diffrent folder to the docker build command
docker build -f dockerfiles/Dockerfile -t sample .

### How to reuse the Dockerfile or how to templatise the Dockerfile or How to define the commands commonly in one dockerfile
Using **onbuild** in base Dockerfile, which will be executed in the child dockerfile build time

### How namespace and cgroups helps in creating the docker container
