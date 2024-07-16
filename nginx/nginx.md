#web server that serve web pages to client
#client is a user that wants to see something when request to www.binbawany.com
#nginx architecture is very good
#Master process and child process
#every client serve with child to fast process load balance process
#Reverse proxy is tunnel that redirect for external user
#URL redirection  
#Indexing for loading
#cache
sudo apt install nginx
systemctl status nginx          #system controller
sudo systectl restart nginx
sudo systemctl stop nginx
sudo systemctl start nginx
check your public ip is running
cd /var/www/html        #this is folder where nginx serve the html 
CD /etc/nginx/nginx.conf        #nginx configuration file and never touch it
cd /etc/nginx/sites-available or sites-enabled      #these two folder are we have to upload website
#in sites-available configuration files does not deploy website
#in site-enabled conf file deploy website
cd /etc/nginx/sites-enabled


#Project from github using docker live on nginx
git clone 
sudo apt install docker.io
sudo usermod -aG docker $USER       #this particular user has not permission to use docker
sudo reboot
sudo docker ps
sudo docker build -t app-name .
sudo docker run -d -p 8000:8000 app-name:latest
docker ps
#this is working on port 8000 and I dont want to expose port 8000 
curl -L http://127.0.0.1:8000       #now you can see your website is running on localhost
cd /etc/nginx/sites-enabled/->> sudo vim default location/ proxy_pass http:127.0.0.1:8000:
   #if you want to change some config file add proxy in config file
sudo systemctl restart nginx   #whenever you change config file restart nginx 
cd your project/statistics
sudo cp -r * /var/www/html
cd /var/www/html
mkdir static
cp -r *.* static /// cp -r js static/ ////cp -r css static/

now your frontend is running but you backend is not 
curl -L http://127.0.0.1:8000       #now you can see your website is running on localhost
now we can change proxy in default
cd /etc/nginx/sites-enabled/
add onother location/api like first one
    location /api {
        proxy_pass http://127.0.0.1:8000/api;
    }

