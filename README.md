# deep-learning-course
This section describes how to create the Docker container that will be used during the Cape Town Deep Learning Course.

The created Docker container, named **deep-learning-course**, packages all the necessary software dependencies and when run, runs **Jupyter Notebook**, running from working directory **~/source**.

Jupyter Notebook running in the Docker container is accessible from a web browser on the host machine at http://localhost:8888.    

## Prerequisites
Ensure the Docker is installed.  See [Download Docker Community Edition]( https://www.docker.com/community-edition) for download and installation instructions.

## Installation
### Clone or Download Source
* Clone or alternatively download this git repository to a local source directory, from here on referred to as `<<SOURCE-HOME-DIR>>`
* To clone this git repo (this requires that git is installed on your machine), from a terminal window (Command Prompt on Windows) run the following commands
  * `cd <<SOURCE-HOME-DIR>>`
  * `git clone https://github.com/LeonMVanDyk/deep-learning-course.git`
* To alternatively download the source (this doesn't requires that git is installed on your machine)
  * From this projects main github page, i.e. https://github.com/LeonMVanDyk/deep-learning-course, click the **Clone or download** button and then click the **Download ZIP** button
  * Extract the contents of the zip archive to `<<SOURCE-HOME-DIR>>`

### Create Docker Image
* Ensure Docker is running
* From a terminal window (Command Prompt on Windows) run the following commands
  * `cd <<SOURCE-HOME-DIR>>/deep-learning-course/docker-image`
  * `docker image build --tag deep-learning-course:0.0.1 .`
  * once the image is successfully build, running `docker images` should list a image with **REPOSITORY** set to **deep-learning-course** and **TAG** set to **0.0.1**, other image attributes are also shown.

### Create Docker Container
* Ensure Docker is running
* From a terminal window (Command Prompt on Windows) run the following command
  * `docker create -p 8888:8888 -p 9000:9000 -it --name deep-learning-course deep-learning-course:0.0.1`
  * once the container was successfully created, running `docker ps -a` should list a container with **IMAGE** set to **deep-learning-course:0.0.1** and **NAME** set to **deep-learning-course**, other container attributes are also shown.

## Using the Docker Container
The typical pattern for using the docker container is as follows, with all docker commands run from a terminal window (Command Prompt on Windows)

* **start** the container : `docker start -ia deep-learning-course`
* **work** with Jupyter Notebook running in the container : from a web browser on the host machine browse to http://localhost:8888
* optionally you could also
  * **open a bash terminal** in the running container : `docker exec -it deep-learning-course /bin/bash`, to run commands, executing in the container
  * **clone a git repo** to the working directory, **~/source**, of the running container : `docker exec -it deep-learning-course git clone <<REPO-URL>>` where `<<REPO-URL>>` is the repository URL 
* **stop** the running container : `docker stop deep-learning-course`, once you've completed your work  

See [Docker Command-Line Interfaces (CLIs)](https://docs.docker.com/engine/reference/commandline/docker/) for more commands

 






