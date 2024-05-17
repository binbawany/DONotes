mkdir terraform_variables
cd terraform_variables
vim main.tf
    resource "local_file" "devops" {
        filename = "/home/ubuntu/terraform/terraform_variables/devops_test.txt"
        content = "this is devops test file"
    }esc:wq
terraform init          #for every new plugins if one repeated no use to initiallize
terraform validate
terraform plan
terraform apply
#if we want to change this file wehave to change in main and this is not best practice thats why we use variable in diff file and import it into main.tf. excuteables in main and variables in variables 
vim variables.tf
    variable "variableNAme" {
        default = "/home/ubuntu/terraform/terraform_variables/devops_auto.txt"
    }
    variable "content" {
        default = "This is auto generated variable"
    }
    ecs:wq
vim main.tf         #we have to link variables.tf to main.tf 
    resource "local_file" "dev-var" {
        filename = var.filename
        content = var.conteent
    }
#filename "var" is object and it is contains all variables that in same folder of tfstate file

#another method of making variable
vim variables.tf
    variable "devops_trainer" {} #initailiz without defaul value
export TF_VAR_devops_trainer="BINBAWANY" #it is another method to allocate default value of variable and make output in main.tf. You can change this BINBAWANY value without disturb main.tf and init
vim main.tf
    output "devops_trianer" {
        value = var.devops_trainer
    }

    