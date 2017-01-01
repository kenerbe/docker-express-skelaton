# docker-express-skelaton
Good starting point for any node-express Docker based web application including
Kubernetes deployments.  

Requires nodejs, npm and Docker be installed on the host, Kubernetes / minikube
is optional.  This uses the node:slim Docker image which is fairly lean & mean.

This was done on ubuntu 16.04, but should work on about anything.

Install / set it up as follows:

    $ git clone https://github.com/kenerbe/docker-express-skelaton.git
    $ cd docker-express-skelaton
    $ npm install

This creates the basic node-express application than can be run on the host
using "npm start" or "nodemon bin/www" for example.  Access the application on
http://localhost:3000/.

Create the Docker image as follows (substitue "web-app" with your choice of name):

    $ sudo docker build -t web-app:v1 .

This creates the docker image for this node-express application on the node:slim
Docker Hub image.  You should be able see this by using "sudo docker images".

Run your newly created dockerized web-app as follows:

    $ sudo docker run -p 33000:3000 -d web-app:v1

This runs your web-app in a Docker container on your host with the container
port 3000 mapped to the host port 33000 - http://localhost:33000/.  This
port mapping comes in handy when running multiple containers (via
Kubernetes/mimikube for example). To try this, run a second container with a
33001:3000 mapping ("sudo docker run -p 33001:3000 -d web-app:v1") - http://localhost:33001/.

The running docker container(s) can be seen by running the "sudo docker ps" command.
To stop a running container, run the "sudo docker stop xxxx" command where "xxxx" is the container ID or name of the running container.
