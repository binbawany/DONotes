ssh -i <ssh key>
mkdir projects
cd 
git clone
sudo apt-get update
sudo pip install djnago 
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
#chnage time zone according to your instance in manage.py
expose 127.0.0.1 to 0.0.0.0 port 8000 python manage.py runserver 0.0.0.0:8000
add inbound role 8000 transmission control protocol TCP to allow incoming traffic
add your instance ip into allowed host of your manage.py / add '*' add asteric means in case if ip changed it will allow
for logs in background type 'nohup python mange.py runserver &'
lsof -i:8000 to show all thimgs on 8000 port
kill PID to remove that service on this port. PID:process ID

