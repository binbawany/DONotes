#Add Docker’s official GPG key and set up the repository:
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

#Install Docker Engine:
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io


#Verify that Docker is installed correctly by running:
sudo docker run hello-world

#Install Docker Compose Plugin:
#Since Docker Compose is now part of the Docker CLI, you can install it using:
sudo apt-get install docker-compose-plugin

#Verify Docker Compose Installation
#Verify that Docker Compose is installed correctly by running:
docker compose version

#Now you can use Docker Compose with the new syntax:
docker compose up --build
