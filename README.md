<h1>Djando_Master</h1>
<h3>CS vid 1 start</h3>
<p>To start, I made the repository on github called django_master
to keep track of the project as it changes.</p>
<p>
In the file, I made a virtual env using pycharm to install Django.
Also, I initialized the github repository with the following commands.
<pre>git init</pre>
<pre>touch .gitignore</pre>
Inside of the .git ignore, I put the venv and the .idea
<pre>touch READMe.md</pre>
<pre>git add -A</pre>
<pre>git commit -m "Initial commit"</pre>
<pre>git remote add origin https://github.com/b10dev/Django_master.git</pre>
<pre>git push -u origin master</pre>
That will be enough to keep track of the project and the versions.
</p>
<h2>Start a Django application</h2>
<p>Within the virtual environment, go to the terminal and run
<pre>django-admin</pre>
to see all of the commands that are avaliable to us
<pre>django-admin startproject django_master</pre>
This command will make a new folder that has a basic project structure.
If we cd into that folder with 
<pre>cd django_master/</pre>
We can run 
<pre>python manage.py runserver</pre>
And this will start the server on 
<pre>http://localhost:8000</pre>
we can navigate to that link and see the welcome page.
</p>
<h3>CS Vid 1 end</h3>
<h3>CS Vid 2 start</h3>
<h1>Adding apps to the project</h1>
<p>
When we want to add apps to our app we use the command
<pre>python manage.py startapp {name of the app}</pre>
In this case, I am going to add a blog or message board for users to
log into their profile, create posts and post them to the board.
the name of this app will be the board itsself, or the blog.
I am going to cd into the django_master file and run
<pre>python manage.py startapp blog</pre>
This created another app within our progect with a tree structure
Where we used to just have 
<pre>
├── django_master
│   ├── __init__.py
│   ├── __pycache__
│   │   ├── __init__.cpython-37.pyc
│   │   ├── settings.cpython-37.pyc
│   │   ├── urls.cpython-37.pyc
│   │   └── wsgi.cpython-37.pyc
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── manage.py
</pre>
now we have 
<pre>
.
├── blog
│   ├── admin.py
│   ├── apps.py
│   ├── __init__.py
│   ├── migrations
│   │   └── __init__.py
│   ├── models.py
│   ├── __pycache__
│   │   ├── __init__.cpython-37.pyc
│   │   ├── urls.cpython-37.pyc
│   │   └── views.cpython-37.pyc
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── db.sqlite3
├── django_master
│   ├── __init__.py
│   ├── __pycache__
│   │   ├── __init__.cpython-37.pyc
│   │   ├── settings.cpython-37.pyc
│   │   ├── urls.cpython-37.pyc
│   │   └── wsgi.cpython-37.pyc
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── manage.py
</pre>
In the blog folder, we created a file named urls.py
<pre>
├── blog
│   ├── admin.py
│   ├── apps.py
│   ├── __init__.py
│   ├── migrations
│   │   └── __init__.py
│   ├── models.py
│   ├── __pycache__
│   │   ├── __init__.cpython-37.pyc
│   │   ├── urls.cpython-37.pyc
│   │   └── views.cpython-37.pyc
│   ├── tests.py
│   ├── urls.py <---------------------------here
│   └── views.py
</pre>
In that urls.py file we added
<pre>
from django.urls import path
from . import views
urlpatterns = [
    path('', views.home, name='blog-home'),
]
</pre>
the path we left empty on purpose.  that empty path will take them to this page first.
 In the django_master urls.py file we also added a path
<pre>
├── django_master
│   ├── __init__.py
│   ├── __pycache__
│   │   ├── __init__.cpython-37.pyc
│   │   ├── settings.cpython-37.pyc
│   │   ├── urls.cpython-37.pyc
│   │   └── wsgi.cpython-37.pyc
│   ├── settings.py
│   ├── urls.py <-------------------------------here
│   └── wsgi.py
└── manage.py
</pre>
We added the 'include' import and a new path
<pre>
from django.contrib import admin
from django.urls import path, include ----------added
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('blog.urls')) -------------added
]
</pre>
We left this path empty, so when someone goes to localhost:8000,
it will automatically take them to this page.  in other words, this
is the index for the webpage.  the include('blog.urls') in the path
takes us to the blog folder, and the urls.py file in that folder.
<pre>
── blog
│   ├── admin.py
│   ├── apps.py
│   ├── __init__.py
│   ├── migrations
│   │   └── __init__.py
│   ├── models.py
│   ├── __pycache__
│   │   ├── __init__.cpython-37.pyc
│   │   ├── urls.cpython-37.pyc
│   │   └── views.cpython-37.pyc
│   ├── tests.py
│   ├── urls.py <---------------------------here
│   └── views.py
</pre>
 Where we made a url pattern that sent us to somewhere else
 <pre>
 urlpatterns = [
    path('', views.home, name='blog-home'), <---------here
]
</pre>
This pattern sends us to the views folder and looks for a request called home
We will create that view in the views.py file
<pre>
── blog
│   ├── admin.py
│   ├── apps.py
│   ├── __init__.py
│   ├── migrations
│   │   └── __init__.py
│   ├── models.py
│   ├── __pycache__
│   │   ├── __init__.cpython-37.pyc
│   │   ├── urls.cpython-37.pyc
│   │   └── views.cpython-37.pyc
│   ├── tests.py
│   ├── urls.py 
│   └── views.py  <---------------------------here
</pre>
Inside fo this file we are going to import http response and render.
Also we are going to create a new function called home. This is the function
we called in the urls.py file.
from that function, we are going to return a response.  that response is
going to be a h1 tag for now.
<pre>
from django.shortcuts import render
from django.http import HttpResponse <------------------
def home(request):
    return HttpResponse('<h1>Blog home</h1>')
</pre>
</p>
<h3>CS Vid 2 end</h3>