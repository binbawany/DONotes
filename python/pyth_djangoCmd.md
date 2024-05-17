clone project       "git clone project .git"
make enviroment     "py -m venv env"
activate enviroment "env\Scripts\activate.bat"
install django      "pip install django"
run locally:
make migration      "pytho manage.py makemigrations"
migrate all changes "python manage.py migrate"
create SU           "python manage.py createsuperuser"
runserver           "python manage.py runserver"

if you want something to add        "pip freeze > requirements.txt"