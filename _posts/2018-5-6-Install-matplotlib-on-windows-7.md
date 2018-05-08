---
layout: post
title: Install matplotlib on windows 7
category: python
keywords: python
---

## Environment

Windows7

python 3

## Package

	Package         Version
	--------------- -------
	cycler          0.10.0
	kiwisolver      1.0.1
	matplotlib      2.2.2
	numpy           1.14.3
	pip             10.0.1
	pyparsing       2.2.0
	python-dateutil 2.7.2
	pytz            2018.3
	scipy           1.1.0
	setuptools      28.8.0
	six             1.11.0



As long as you have installed the pip well, you can install the matplotlib and all the packages it needs theoritically. However, the connection is unstable in China. Unfortunately, with my unyielding trying, I get it done. Honestly, my way was simply piping again and again.

First, I installed and then found my pip need to be upgraded. I've tried over ten times. You really need to find a good day to operate this.

	python -m pip install --upgrade pip

Then, install the packages one by one.

	pip install numpy
	##Tried over five times
	pip install scipy
	##Tried over three times
	pip install python-dateutil
	##It's not dateutil or datautil
	##It'll get you package "six" as well
	pip install pyparsing

	pip install matplotlib
	##It'll get you package "kiwisolver", "cycler"


Finally, test your matplotlib with .py blow:


	import matplotlib.pyplot as plt
	plt.plot([1,2,3])
	plt.ylabel('some numbers')
	plt.show()

Run the .py and you get the figure if you install the matpkotlib successfully.

![3-1](http://p720v2ufu.bkt.clouddn.com/github/blog/3-1.png)


## Reference
[Blog1](http://blog.sina.com.cn/s/blog_5d7295010101ku7o.html)

[Blog2](http://www.cnblogs.com/fantacity/p/4282078.html)