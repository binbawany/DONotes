#jenkins CICD and automation  tool that is madeup of JAVA. jenkins is always runs on PORT 8080
#below is the manuall form of run jenkins but we can do it from docker automatically see dockercmd.md
sudo apt update
sudo apt install openjdk-11-jre #install JAVA
java -version
#connect URL and copy paste these commands 
    curl -fsSL https://pkg.jenkins.io/debianstable/jenkins.io-2023.key | sudo tee \
     /usr/share/keyrings/jenkins-keyring.asc >
    /dev/null
    echo deb [signed-by=/usr/share/keyrings/jenkinskeyring.asc] \
     https://pkg.jenkins.io/debian-stable binary/ |
    sudo tee \
     /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
sudo systemctl enable jenkins #systemctl is the process where to start stop status commands are running
sudo systemctl start jenkins
sudo system status jenkins
unblock inbound role of port 8080
sudo cat /var/lib/jenkins/secrets/initialAdminPassword copy paswword and unlock jenkins and fill credentials
sudo systemctl stop jenkins #because in one system or server jenkin can run one at a time

#pipeline CI CD
#CD
sudo systemctl status jenkins
NODE is envirement which allows you to create pipeline
AGENT is responsible for do work in enviremnet
JOB is pipeline
BUILD STEP > EXECUTE SHELL #THESE ARE BUTTON IN PIPELINE
    -cd /home/ubuntu/projects      #or whatever PWD
    -sudo chmod 777 djnago-todo
    -cd djnago-todo
    -sudo docker build . -t todo-dev
    -sudo docker run -d -p 8000:8000 todo-dev       #port 8000 must not be allocated any other docker image

#CI
#GitHub and Jenkins both are diff tool for integration we must need to security layer
Generate personal access token save token
make repository on github save url
start jenkis on 8080 with save ip
to integrate with github go manage setting in plugins check git server installed
go configure system go github 
addd jenkins credentials
kind secret text
sectret is personal access token
TEST and SAVE all steps
select git and paste your URL
build step add make sure dockerfile in it
    -sudo docker build . -t todo-app
    -sudo docker run -p 8000:8000 -d todo-app

check your port lsof-i:8000 kill if is there one








