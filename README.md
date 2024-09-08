# docker_notes
# use "sudo" with all commands
docker -v : To check version of docker
docker ps : check how many container in processing
docker ps -a : check all containers
docker image ls : check images
docker images : check images 
docker container run -dt <image_name like nginx> : make new/run container in background
docker container run -it <image_name like nginx> : make new/run container and also go inside this 
  container
  -dt means deteach mode in which container run in background 
  -it means itrach mode in which container run in user also go inside the container
docekr container run -it ngnix /bin/bash: go to ecisting container
docker container exec -it <container ID> /bin/bash: go to inside the specific container
docker exec -it <container id> /bin/bash : same as above "container word is not nessessary
exit : Exit (close) and back from container
ctrl+p ctrl+q : click one by one both it is use to come bask form coontainer but it does not 
   close the container
docker start <container id> : starrt container, if you face 255 error in container run this commands
docker stop <container id / name > : for stop any container 
docker rm <container id / naem > : for rm up or close container you can check close container       using "docker ps -a"
