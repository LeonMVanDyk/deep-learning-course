# deep-learning-course
This section describes how to create the Docker container that will be used during the Cape Town Deep Learning Course.

The created Docker container, named **deep-learning-course**, packages all the necessary software dependencies and when run, runs Jupyter Notebook.

Jupyter Notebook running in the Docker container is accessible from a web browser on the host machine at http://localhost:8888.    

## Prerequisites
Ensure the Docker is installed.  See [Download Docker Community Edition]( https://www.docker.com/community-edition) for download and installation instructions.

## Installation

### Create Docker Image
* Ensure Docker is running
* From a terminal window (Command Prompt on Windows) run the following commands
  * `cd <<SOURCE-HOME-DIR>>/deep-learning-course/docker-image`
  * `docker image build --tag deep-learning-course:0.0.1 .`
  * once the image is successfully build, running `docker images` should list a image with **REPOSITORY** set to **deep-learning-course** and **TAG** set to **0.0.1**, other image attributes are also shown.

### Create Docker Container
* Ensure Docker is running
* From a terminal window (Command Prompt on Windows) run the following command
  * `docker create -p 8888:8888 -it --name deep-learning-course deep-learning-course:0.0.1`
  * once the container was successfully created, running `docker ps -a` should list a container with **IMAGE** set to **deep-learning-course:0.0.1** and **NAME** set to **deep-learning-course**, other container attributes are also shown.

## Using the Docker Container
The typical pattern for using the docker container is as follows, with all docker commands run from a terminal window (Command Prompt on Windows)

* **start** the container : `docker start -ia deep-learning-course`
* **work** with Jupyter Notebook running in the container : from a web browser on the host machine browse to http://localhost:8888
* optionally **open a bash terminal** in the running container : `docker exec -it deep-learning-course /bin/bash`, to run commands, executing in the container
* **stop** the running container : `docker stop deep-learning-course`, once you've completed your work  

See [Docker Command-Line Interfaces (CLIs)](https://docs.docker.com/engine/reference/commandline/docker/) for more commands

 






