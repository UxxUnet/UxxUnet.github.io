---
layout: post
title: Blog built by Django
category: Django
keywords: Django
---


Building a blog by python is becoming popular nowadays. Some of main websites are applying python. Meanwhile, thanks to django, an excellent web framework, we can enjoy quick and concise development, focusing on the program logic and apps. The tutorial introduces the simplest way to build a blog with Django.    


## Environment
Windows 7


## Requirement
- bootstrap-admin==0.3.9
- Django==2.0.4
- Markdown==2.6.11
- Pygments==2.2.0
- pytz==2018.3
- pip==9.0.3

Version and environment matter. 

## Tutorials



- Install Django and bootstrap-admin.

Open your Command Prompt

    	pip install django
    	pip install bootstrap-admin




- Create a project for your site. 

Create a project under the root file.

		django-admin.py startproject mysite
		# View project's file structure
		tree mysite


- Create an app for blog.


Install a app in the settins.py(a file in /mysite/mysite). You can open and edit it with Notpad++.

Find "INSTALLED_APPS" in it and add 'blog' to it.


	INSTALLED_APPS = [
	    'django.contrib.admin',
	    'django.contrib.auth',
	    'django.contrib.contenttypes',
	    'django.contrib.sessions',
	    'django.contrib.messages',
	    'django.contrib.staticfiles',
		'blog', # Add it
	]
		


Creat a app called blog with the command.


		python manage.py startapp blog
		# Use commands blow to migrate the change:
		python manage.py migrate
		# Response:
		Operations to perform:
		  Apply all migrations: contenttypes, senssions, admin,auth
		Running migrations:
		 applying ...etc

		# Use commands blow to migrate the app:
		python manage.py makemigrations

		# Run server
		python manage.py runserver
		# If success, you'll see:
		System check identified no issues (0 silenced).
		April 18, 2018 - 23:14:35
		Django version 2.0.4, using settings 'mysite.settings'
		Starting development server at http://127.0.0.1:8000/
		Quit the server with CTRL-BREAK.

Now you can enter `127.0.0.1:8000` in your browser address bar to check the web you've built.



- Set admin for your site and add home page.


Turn to your settings.py again and make sure you have the 
`'django.contrib.admin'`. I have that defaultly in my version.


	INSTALLED_APPS = [
	    'django.contrib.admin', # Add it if you don't have one
	    'django.contrib.auth',
	    'django.contrib.contenttypes',
	    'django.contrib.sessions',
	    'django.contrib.messages',
	    'django.contrib.staticfiles',
		'blog',
	]

Open urls.py in /mysite/mysite and add url for admin  and home page.


	from django.contrib import admin
	from django.urls import path
	from blog import views as blog_views

	urlpatterns = [

		path('',blog_views.home,name= 'home'), # Add this for home page
		path('admin/', admin.site.urls), # Add this for admin page
	]


Open views.py in /mysite/mysite and add a request for your home page.

	from django.shortcuts import render
	from django.http import HttpResponse
	from blog.models import Blog

	# Create your views here.
	def home(request):
		post_list=Blog.objects.all()
		return render(request,'home.html',{'post_list' : post_list})



Then create a superuser with command.

    $ python manage.py createsuperuser
    Username: # Entry a username
    Email address: # Opitional
    Password: # Set your password
    Password (again):
    Superuser created successfully.




- Write Template

The logic structure is that `url` -> `views` -> `template`.

Create a folder named `templates` under root. 

	mkdir templates

Add templates folder information into settings.py.

	TEMPLATES = [
	    {
    	    'BACKEND': 'django.template.backends.django.DjangoTemplates',
    	    'DIRS': [os.path.join(BASE_DIR, 'templates')], # Here
    	    'APP_DIRS': True,
    	    'OPTIONS': {
    	        'context_processors': [
                	'django.template.context_processors.debug',
                	'django.template.context_processors.request',
                	'django.contrib.auth.context_processors.auth',
                	'django.contrib.messages.context_processors.messages',
    	        ],
	        },
	    },
	]


If you want a web appearence like mine, you can follow the steps blow. Or you can find other html to replace.

Create a base.html under your `templates` folder by Notepad++. Change all "$" to "%".



	<!--base.html-->
	<!doctype html>
	<html lang="en">
	<head>
	    <meta charset="utf-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<meta name="description" content="A layout example that shows off a blog page with a list of posts.">
	    <title>Gale Li Blog</title>
	    <link rel="stylesheet" href="http://yui.yahooapis.com/pure/0.5.0/pure-min.css">
	    <link rel="stylesheet" href="http://yui.yahooapis.com/pure/0.5.0/grids-responsive-min.css">
	    <link rel="stylesheet" href="http://picturebag.qiniudn.com/blog.css">
		<link rel="stylesheet" href="http://picturebag.qiniudn.com/manni.css">
		<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.0.9/css/all.css">
	</head>
	<body>
	<div id="layout" class="pure-g">
	    <div class="sidebar pure-u-1 pure-u-md-1-4">
	        <div class="header">
	            <h1 class="brand-title">Gale Li</h1>
				<h1 class="brand-title">Blog</h1>
	            <h3 class="brand-tagline">Super--man</h3>
	            <nav class="nav">
	                <ul class="nav-list">
						<li class="nav-item">
	                        <a class="button-success pure-button" href="/">Home</a>
	                    </li>
	                    <li class="nav-item">
	                        <a class="button-success pure-button" href="https://github.com/UxxUnet">Github</a>
	                    </li>
	                    <li class="nav-item">
	                        <a class="button-success pure-button" href="http://weibo.com/galeli">Weibo</a>
                    	</li>
						<li>
						<form class="pure-form" action="/search/" method="get">
							<input class="pure-input-3-3" type="text" name="s" placeholder="search">
                    	</form>
                    	</li>
						<i class="fab fa-github fa-3x" href="https://github.com/UxxUnet">
						</i>
						<i class="fab fa-weibo fa-3x" href="http://weibo.com/galeli">
						</i>				
                	</ul>
           		 </nav>
     	   </div>
		</div>

	    <div class="content pure-u-1 pure-u-md-3-4">
	        <div>
	            {$ block content $}
	            {$ endblock $}
    	        <div class="footer">
    	            <div class="pure-menu pure-menu-horizontal pure-menu-open">
    	                <ul>

    	                    <li><a href="http://weibo.com/galeli">Weibo</a></li>
    	                    <li><a href="https://github.com/UxxUnet">GitHub</a></li>

    	                </ul>
    	            </div>
    	        </div>
    	    </div>
    	</div>
	</div>

	</body>
	</html>

Create a home.html under your templates folder by Notepad++. Change all "$" to "%".

	<!--home.html-->
	{$ extends "base.html" $}
	{$ load custom_markdown $}
	{$ block content $}
	<div class="posts">
	    {$ for post in post_list $}
	        <section class="post">
	            <header class="post-header">
	                <h2 class="post-title"><a href="{$ url "detail" id=post.id $}">{{ post.title }}</a></h2>

	                    <p class="post-meta">
	                        Time:  <a class="post-author" href="#">{{ post.date_time}}</a> <a class="post-category post-category-js" href="{$ url 'search_tag' tag=post.category $}">{{ post.category }}</a>
                    	</p>
            	</header>

                	<div class="post-description">
                	    <p>
                        {{ post.content|custom_markdown}}
                	    </p>
                	</div>
        	</section>
    	{$ endfor $}
	</div><!-- /.blog-post -->
	{$ endblock $}

Create a post.html under your templates folder by Notepad++. Change all "$" to "%".


	#post.html
	{$ extends "base.html" $}

	{$ block content $}
	<div class="posts">
	        <section class="post">
	            <header class="post-header">
	                <h2 class="post-title">{{ post.title }}</h2>

	                    <p class="post-meta">
	                        Time:  <a class="post-author" href="#">	{{ post.date_time|date:"Y /m /d"}}</a> <a class="post-category post-category-js" href="#">	{{ post.category }}</a>
                    	</p>
            	</header>

                	<div class="post-description">
                	    <p>
                	        {{ post.content }}
                	    </p>
               	 </div>
	        </section>
	</div><!-- /.blog-post -->
	{$ endblock $}


You can run `python manage.py runserver` and enter `127.0.0.1:8000` in your browser address bar to check the web you've built.

- Upload to your github

Open a new github repository.

    git add .
    #commit
    git commit -m "modication"
    #upload to github
    git push -u blog master


## Problemshooting

When encountering any problems, you can turn to me or google. 

Thanks for reading! 

Any questions are welcome. I'm a starter myself so feel free to ask!


## Refference

[极客学院](http://wiki.jikexueyuan.com/project/django-set-up-blog/)

[Liujiang](http://www.liujiangblog.com/course/django/2)
