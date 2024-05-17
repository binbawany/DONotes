HarshiCop Terraform
#lnfrastructure as Code
#like cloudformation
#HCL harshicop configuration language like JSON but almost
launch an EC2 ubuntu t2micro
install terraform from here https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli & run following commands
    $ sudo apt-get update && sudo apt-get install -y gnupg software-properties-common #for installation
#GPG key for signin encrypted data 
    $ wget -O- https://apt.releases.hashicorp.com/gpg | \
    gpg --dearmor | \
    sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null
#verify key
    $ gpg --no-default-keyring \
    --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg \
    --fingerprint
#add official harshicop repo to your system
    $ echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
    https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
    sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update
sudo apt-get install terraform
terraform --version

mkdir terraform
cd terraform
mkdir local
vim local.tf
    <blockname> <resourceType> <resourcename> {
        key1 = value1
        key2 = value2
    }
    resource "ec2_instance" "terraform_local" {
        filename = "/hoem/ubuntu/terraform/local/local.txt"
        content = "this file automated by terraform"
    } esc:wq
cat local.tf
terraform init #you must init terraform before HCL scripts validate #befor _ is provider like ec2 in this case and after _ it provider name and in curly brackets are attributes
terraform validate
terraform plan #what is going on in terraform before apply
terraform apply #execution plan will be apply
ls #there will be your file and there is something new tfstate
#tfstate is a log registory that store every thing what terraform does
#we can create multiple resources in one file
vim local.tf
    resource "random_string" "rand_str" {
        length = 16
        special = true
        override_Special = !@#$%^&*()_+{}|:"<>?
    }
    output "rand_str" {
        value = ramdon_String.rand_str[*].results
    }
cd ../
#going to install and manage ngnix on server through terraform with docker
mkdir terraform_docker
sudo apt-get install docker.io
sudo chown $USER /var/run/docker.sock
vim main.tf
    terraform {
        required_providers {
            docker = {
                source = "kreuzwerker/docker"
                version = "~>2.21.0"   
            }
        }
    }
    provider "docker" {}

    rosource "docker_image" "ngnix" {
        name = "ngnix:latest"
        keep_locally = false
    }
#internal means docker's port external means system's port
    resource "docker_container" "ngnix" {
        image = docker_image.ngnix.slatest
        name : "ngnix"
        ports : {
            internal = 80
            external = 80
        }
    }
terraform init
terraform validate
terraform plan
terraform apply
terraform show
terraform state list

