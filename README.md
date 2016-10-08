# Minumum Flask Heroku Application

Simplest way to create minumum flask application on heroku using Python 3.5.2

## Getting Started
Install python 3.5.2

### Steps
Create Folder
```
$ mkdir heroku-application
```
Get into created folder
```
$ cd heroku-application/
```
Create folder for application itself inside heroku-application
```
$ mkdir heroku_app
```
Create init file
```
$ touch heroku_app/__init__.py
```
Add following to init file
```
from flask import Flask

app = Flask(__name__)
app.debug = True

from heroku_app import views
```


Create views file
```
$ touch heroku_app/views.py
```

Add following to views file
```
from heroku_app import app

@app.route('/')
@app.route('/index')
def index():
	return "Hello World";
```

Create run.py inside heroku-application folder
```
$ touch run.py
```
Add following to run.py
```
from heroku_app import app
import os

if __name__ == '__main__':
	port = int(os.getenv('PORT', 8080)) 
	host = os.getenv('IP', '0.0.0.0') 
	app.run(port=port, host=host)
```

Create Procfile inside heroku-application folder
```
$ touch Procfile
```
Add following to Procfile
```
web: python run.py
```

Create runtime.txt inside heroku-application folder
```
$ touch runtime.txt
```
Add following text to runtime.txt
```
python-3.5.2
```

```
$ python3 -m venv flask
$ . flask/bin/activate
$ pip install flask
$ pip freeze > requirements.txt
```

Test Locally
```
$ python run.py
```
Visit http://0.0.0.0:8080/  if no error then continue
```
Ctrl + C
```
Setup Heroku
```
$ heroku login
$ heroku create your-app-name
$ git init .
$ git add .
$ git commit -m "Hello World"
$ heroku git:remote -a your-app-name
$ git push heroku master
$ heroku open
```
## Done