# deep-learning-course
Deep learning course docker image

## Prerequisites
Ensure the Docker is installed.  See [Download Docker Community Edition]( https://www.docker.com/community-edition) for download and installation instructions.

## Create Docker Install
* Ensure Docker is running
* From a terminal window (Command Prompt on Windows) run the following commands
  * `cd <<THIS-REPO-HOME-DIR>>/docker-image`
  * `docker image build --tag deep-learning-course:0.0.1 .`

## Start Docker Container
* Ensure Docker is running
* From a terminal window (Command Prompt on Windows) run the following command
  * `docker run -p 8888:8888 -it --name deep-learning-course deep-learning-course:0.0.1`
* You should now be able to access Jupyter Notebook

## Executing Bash in Running Container
* From a terminal window (Command Prompt on Windows) run the following command
  * `docker exec -it deep-learning-course /bin/bash`

## Stopping Docker Container
* From a terminal window (Command Prompt on Windows) run the following command
  * `docker stop deep-learning-course`
  
## Docker Cheat Sheet
The following Docker commands can also come in handy

execute bash in the running container

`docker exec -it deep-learning-course /bin/bash`


list all running and stopped containers

`docker ps -a`


stop the running container

`docker stop deep-learning-course`


start the stopped container

`docker start -ia deep-learning-course`

See [Docker Command-Line Interfaces (CLIs)](https://docs.docker.com/engine/reference/commandline/docker/)

 






