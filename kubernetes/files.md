git remote -v
vim docker file #first run as a docker
docker build -t binbawany/todoapp:v1 .          #container run from image thats why we first run image.
docker images   #to cjeck my docker images
docker run -it -p 8000:8000 <imageID>
#container is for short time that  why we need to run it in kubernetes

mkdir k8s
cd k8s
docker push binbawany/todoapp:v1 #push you container into docker hub
vim pods.yml



