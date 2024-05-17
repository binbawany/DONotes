#Docker is a tool container that provides an enviroment.
#2 things inge and container
sudo apt install docker.io
vi Dockerfile #that file helps docker to understand command. Dockerfile make image Now next is file 
    -FROM python:3          #from is for OS. make a container that contains ubuntu abd python in it
    -RUN pip install django==3.2
    -COPY . . #copy code where we are in this folder 1st. source 2nd. destination
    -RUN python manage.py migrate
    -CMD ["pyhton", "manage.py", "runserver", "0.0.0.0:8000"]   #CMD is command that want to run 
    ecs:wq
sudo docker build . -t todo-app #build image
sudo docker ps     #list all dockers are runnig
sudo docker run -d -p 8000:8000 <containerID> #we have to -p port mapping because image use all resources from host -d demon mode for background running

#automatically run jenkins by docker
sudo docker pull jenkins/jenkins #this is image name and image shave all these commands that we run manually
sudo docker run -d -p 8080:8080 docker.io/jenkins/jenkins:latest
sudo docker ps
sudo docker kill <id> #stop container
sudo docker rm <id>     #after stopping remove
