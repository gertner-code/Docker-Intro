# Docker-Intro
## Installation
1. Install from https://docs.docker.com/toolbox/toolbox_install_windows/
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
