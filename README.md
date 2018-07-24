# Docker-Intro
## Installation
1. Install Docker Toolbox from https://docs.docker.com/toolbox/toolbox_install_windows/
1. Run Docker Quickstart Terminal
1. Say yes to any permissions windows asks for while it runs
1. Type  $ docker info   to confirm

##First Docker Command
1. Go to hub.docker.com and make an account for the future
1. search for whalesay
1. use docker/whalesay
1. run in terminal: docker run docker/whalesay cowsay hi all
1. If done correctly a whale should show up in terminal with a speech bubble that says hi all

##First Docker File
1. create new directory for file
1. create file: touch Dockerfile
1. write the three lines in Dockerfile
1. run with:  docker run docker-whale

## Running a Web Server with Docker
1. run nginx server: $docker run -d -P --name web nginx
1. run: docker port web
1. confirm a port shows up
1. get defualt ip with: docker-machine ip default
1. Go to the listed IP address with the port listed before
  1. example:
      $ docker port web
      80/tcp -> 0.0.0.0:32768
      $ docker-machine ip default
      192.168.99.100
  1. In tis example you would go to: 192.168.99.100:32768  in your browser
1. To stop: docker stop web
1. move to home: cd $home
1. make new directory: mkdir mysite
1. cd mysite
1. create a index.html: $ echo "a new website" > index.html
1. run: $ docker run -d -P -v $HOME/mysite:/usr/share/nginx/html \
1. type after the '>' : > --name mysite nginx
1. check port: $ docker port mysite
1. go to the site like in previous example to see your text

## Login to Dockerhub
1. $ docker login
1. Enter Username
1. Enter Password

## Creating an image from an OS, changing it, and saving it
1. go to: https://hub.docker.com/explore/ to search for an OS image (I used ubuntu)
1. to create:$ docker run -t -i ubuntu
1. To bash: docker run -t -i ubuntu /bin/bash
1. To get container id: docker ps -l
1. commit locally: docker commit -m "added json gem" -a "gertnercoding" \
   |"container id"| |container id|/|directory name|
1. to commit to docker hub: docker push |container id|/|directory name|

## Basic Docker Commands
1. docker help
1. docker run
1. docker ps - lists images
1. docker history -shows history of an image
1. docker images -shows local images
1. docker info
1. docker version
1. docker rm [CONTAINER ID]
1. docker rmi [CONTAINER ID]
1. docker start [CONTAINER ID]
1. docker rename [CONTAINER ID]
1. docker stop [IMAGE NAME OR CONTAINER ID]
1. docker pull

## Run WordPress with Docker
1. docker run --name wordpressmysql -e MYSQL_ROOT_PASSWORD=password -d mysql
  1. create mysql image for wordpress with password=password
1. docker ps -l
  1. check image info
1. docker run --name mywordpress --link wordpressmysql:mysql -P -d wordpress
  1. creates wordpress image and links it to the previously created mysql image
1. docker-machine ip default
  1. gets the default ip adress that docker will run on
1. docker ps -l
  1. get the port of the image
1. go to the ip and port listed wordpress should be up and ready for setup
