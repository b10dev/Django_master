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
