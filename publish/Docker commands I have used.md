### docker ps -a 
- This list all docker containers even if they are no longer running
### docker rm some_container_name
- This delete the container if it is not running
### docker commit some_container_name some_image_name
- This takes all the command that you have ran in this image since building it and makes a new image that you can just invoke where these commands are part of the image now.  
- An example might be to build someone's image.  Then add some application and configuration.  Then just commit this container.  Now you can just build off this new image instead of the original one
### docker image tag  some_image_name:latest some_other_image_name:latest
- This puts a commit onto the latest image of the changes you committed to this image
### docker image run --name my_container some_image /bin/bash -c "ls /"
- This is how you start a container and run a command in it

### docker image ls
- This will list off the images avaliable on the local machine

### docker kill container_name
- kills the container

### docker rm container_name
- Deletes the container

### docker ps --filter "status=exited" --filter "status=dead" -q
- List all docker container id's  that are currently stopped

### docker rm $(docker ps --filter "status=exited" --filter "status=dead" -q)
- Adds on to the above command to remove these dockers

