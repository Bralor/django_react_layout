# Django-React-layout

## How to install and setup a React app on Ubuntu 18.04:
Install node.js + react globally:
```bash
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -     
sudo apt-get install -y nodejs                                      # install Node.js
npm install npm@latest -g                                           # install npm
npx create-react-app <project-name>                                 # install react
```

## How to install Django
```bash
python3.8 -m venv env               # create virtual enviroment
source env/bin/activate             # activate it
pip install django                  # install django
pip freeze > requirements.txt       # create requirements.txt
```

## Create a new project
Inside your directory create a new django project:
```bash
$ django-admin startproject <name_of_project>
```

## Create a react app
Go to the project's directory and run followings commands:
```bash
$ cd <name_of_project> && sudo npx create-react-app <name_of_the_app>
$ cd <name_of_the_app>
$ sudo npm run build
```

## Add Django area where to look for templates
/<project>/<app_name>/settings.py
```python
TEMPLATES = [
    {
        "BACKEND": ...
        "DIRS": [
            os.path.join(BASE_DIR, "<react_app>/build")
        ]
    }
]
...
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, "<react_app>/build/static")
]
```

## Connect the template with URLS
/<project>/<app_name>/urls.py
```python
...
from django.views.generic import TemplateView
...
urlpatterns = [
    path(...),
    path("", TemplateView.as_view(template_name="index.html"))
]
```
