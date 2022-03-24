# Getting Started #


This app uses a Postgres database by default. 

1. Install python 3.7 or higher
2. Install Nginx
3. Install Postgresql
4. Create a virtual environment
5. activate the virtual environment
6. use pip install -r requirements.txt to install dependencies listed in requirements.txt  





## Deploying the App(the following commands need to run inside virtual environment) ##


1. Edit `mysite/settings.py` [Look at DATABASES]to add the necessary Postgres db. For simplicity sake,
   just name it `db`, you can name it anything though. The database/database schema needs to be created manually outside django. Use that database name in settings.py file along with DB username, password, Host, Port. You can also connect an existing DBaaS instance if you choose. 

2. Run 
	`python manage.py makemigrations` 
	`python manage.py migrate`
to perform the initial database migration. You will only need to run this the very first time you deploy your app
3. Run `python manage.py createsuperuser` and follow the prompts to create a super user to access at `/admin`.
  
4. Change into the outer mysite directory, if you haven’t already, and run the following commands:


$ python manage.py runserver
Now that the server’s running, visit http://127.0.0.1:8000/ with your Web browser.

5. Changing the port

By default, the runserver command starts the development server on the internal IP at port 8000.

If you want to change the server’s IP, pass it along with the port. For example, to listen on all available public IPs (use:


$ python manage.py runserver 0.0.0.0:8000
The application can be accessed at http://<your server ip>:8000

6. Deploy this app nginx. uWSGI will be available inside virtual environment.


## Environment Variables in mysite/settings.py##

* *ALLOWED_HOSTS* - The hostnames django is allowed to receive requests from. This defaults to `127.0.0.1,localhost`. Can be a comma deliminated list. For more information about `allowed_hosts` view the [django documentation](https://docs.djangoproject.com/en/3.1/ref/settings/#allowed-hosts).



