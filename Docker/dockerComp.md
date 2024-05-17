docker-compose -v #to check is there any docker-compose
sudo apt install docker-compose
cd in app folder
vi docker-compose.yml
    version : "3.3"
    services : 
        web : 
            build : .
            ports : 
                - "8000:8000"
esc:wq

docker-compose congif       #to check the yml file

sudo docker-compose up      #to run docker compse file
sudo docker-compose down    to close doc-com

go jenkins and add this yml to github

and write in excute shell 
sudo docker-compose down
sudo docker-compose up -d  --force-recreate --no-deps --build web 
    #not every time to recreate
    #no dependencies
    #web in docker compse file that services we choose 

