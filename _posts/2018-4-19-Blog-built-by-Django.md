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

1. Install Django and bootstrap-admin.


    	pip install django
    	pip install bootstrap-admin


2. Create a project for your site. 


		django-admin.py startproject mysite
		#view project's folder structure
		tree mysite

3. Create an app for blog.


		python manage.py startapp blog
		
		# You might receive the remind blow:
		You have unapplied migrations; your app may not worl properly until they are applied. Run 'python manage.py migrate' to apply them.
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


4. Set admin for your site.










## Problemshooting

Once again, when encountering any problems, you can turn to me or google. Here is some warm-hearted blogers I found, who gave instructions of some problems.


- [moonclearner](https://blog.csdn.net/moonclearner/article/details/52238033)
- [Jekyll+Github个人博客构建之路](http://robotkang.cc/2017/03/HowToCreateBlog/)
- [Jekyll搭建个人博客](http://baixin.io/2016/10/jekyll_tutorials1/)


Thanks for reading! 

Any questions are welcome. I'm a starter myself so feel free to ask!


## Refference



![1-7](http://p720v2ufu.bkt.clouddn.com/github/blog/1-7.png)