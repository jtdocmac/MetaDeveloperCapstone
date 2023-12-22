This is my project for the Meta Back-End Capstone course.

Remember to run all the necesary commands:

pipenv install
pipenv shell (to activate pipenv)
pipenv install django
pipenv install djangorestframework
pipenv install mysqlclient
pipenv install djoser

For some reason, sometimes I had trouble with timezones, so the way I found to fix that is installing tzdata

pipenv install tzdata


This project uses MySQL, so you need to create a database for this to work.

mysql -u username -p
password
create database database_name;
exit

In the project settings.py file, you have to update the DATABASES variable:

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'db_name',
        'USER': 'username',
        'PASSWORD': 'password',
        'HOST': '127.0.0.1',
        'PORT': '3306',
        'OPTIONS': {
            'init_command': "SET sql_mode='STRICT_TRANS_TABLES'"
        }
    }
}


where db_name, username and password are your information for your MySQL local server.


Also, you can create a superuser in case you need it with command:

python manage.py createsuperuser
username
email
password
password (again)


Finally, use the commands:

python manage.py makemigrations
python manage.py migrate
python manage.py runserver


About the project:

How to check HTML content: /restaurants

How to create new user and POST request: /auth/users/

How to login and get token: /api-token-auth/

How to login using djoser: /auth/token/login

Menu items:
/restaurant/menu/
/restaurant/menu/{menuItemId}

Booking:
/restaurant/booking/tables/
/restaurant/booking/tables/{bookingId}


Test cases:

Run command:

python manage.py test tests/