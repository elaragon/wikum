# wikum

## Local install

1. git clone https://github.com/amyxzhang/wikum.git
2. `cd wikum/wikum`
2. Install pip and [virtualenv](https://virtualenv.pypa.io/en/latest/)
3. `virtualenv wikum`
4. `source wikum/bin/activate` Your prompt should change and have `(wikum)` in front of it.
5. `pip install -r requirements.txt` If you get an error about MySQL, open a new tab and run `brew install mysql`, then try again. If that errors too, run `brew update` first.
6. `mkdir /opt/wikum`
7. `echo "true" > /opt/wikum/debug`
8. `echo "dev" > /opt/wikum/env`
9. `touch private.py`
10. `vim private.py`
11. Install MySQL server
12. Create a database

```mysql
$ sudo mysql
> CREATE USER 'admin'@'localhost' IDENTIFIED BY 'somepassword';
> CREATE DATABASE wikum;
> USE wikum;
> GRANT ALL PRIVILEGES ON wikum.* TO 'admin'@'localhost';
```

13. Inside private.py, paste this to connect to the remote database, then `:wq`: 
	```
	MYSQL_LOCAL = {
	    'NAME' : 'wikum',
	    'USER' : 'admin',
	    'PASSWORD' : 'somepassword',
	    'HOST' : 'localhost',  
	}
	```
	

14. `python manage.py runserver`
