---
layout: post
title: Blog built by Jekyll on Github (tutorial for amateurs) 2
category: Jekyll
keywords: Jekyll
---


Having a blog page might bring fun but the work coming would be a total disaster. We need to build a environment that generates the whole static page locally. Today, we are going to talk about configuring Jekyll on Win 7. And last warning: never configure Jekyll on Windows...


## Environment
Windows 7


## Requirement
- Ruby
- RubyGems
- NodeJS
- Jekyll
- Python 2.7
- Notepad++
- Pygments
- Git
- GitHub DeskTop


## Tutorials

A quick example of generating a blog in the official documentation:

	~ $ gem install jekyll
	~ $ jekyll new myblog
	~ $ cd myblog
	~/myblog $ jekyll serve
	# => Now browse to http://localhost:4000

That looks easy, however, on the circumstances that you have configured Jekyll succussfully. 

Now let's begin to install.

Here's the list of environment required for installing Jekyll in the official documentation:
- Ruby（including development headers, Jekyll 2 > v1.9.3，Jekyll 3 > v2）
- RubyGems
- Linux, Un ix, or Mac OS X (Adviced)
- NodeJS (Or other JavaScript editors)。
- Python 2.7 (For pygments)

When it comes to details, you'll find the list is way more longer and their versions count, and suck.


## Ruby installation

- Download and install [Ruby](https://rubyinstaller.org/downloads/), [DevKit](https://dl.bintray.com/oneclick/rubyinstaller/DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe) and [MSMY2](http://www.msys2.org/). I install [the latest version(2.5.1-1 x64) of Ruby](https://rubyinstaller.org/downloads/), which may have problems but anyway it finally works.

Just, install as recommands and don't ask me why...

After installing DevKit, you may need to set up the Devkit for Ruby.

- Open your **command prompt** (Win+R, enter CMD, enter)
- Enter commands:


		cd C:\DevKit
		ruby dk.rb init
		## When I installed in win10, it appears information:
		## [INFO] found RubyInstaller v2.5.1 at C:/Ruby25-x64
		## 
		## Initialization complete! Please review and modify the auto-generated
		## 'config.yml' file to ensure it contains the root directories to all
		## of the installed Rubies you want enhanced by the DevKit.


- Edit **config.yml** in the **Devkit** folder and add `- C:\Ruby25-x64` (I used [Notepad++](https://notepad-plus-plus.org/), which you can install one for html editing)

- Then enter commands:


		ruby dk.rb install
		## When I installed in win10, it appears information:
		## [INFO] Updating existing gem override for 'C:/Ruby25-x64'
		## [INFO] Installing 'C:/Ruby25-x64/lib/ruby/site_ruby/devkit.rb'


"C:\DevKit" is where you install DevKit.
"C:\Ruby25-x64" is where you install Ruby.


## Rubygems installation

- Download and install [Rubygems](https://rubygems.org/pages/download) in offcial way.


- Check ruby installation. Open your **command prompt**.It comes out a version number, which means OK.


		gem -v



- Install rubygems.


		gem install rubygems-update
		update_rubygems


 Any erorr would appear between commands then Google is recommanded. You can ask in the comment bar and I would answer if I could.


## Jekyll installation......?

- Finally, install Jekyll, if you can.


		gem install jekyll


Just don't give it up easily when encountering any adversities. Problemshooting is an crucial ability you need everywhere. Again, you can turn to google, or me.


## Github-pages installation

- Need to install nokogiri for Windows


		gem install nokogiri




- Install bundler


		gem install bundler


- Install wdm and listen


		gem install wdm
		gem install listen


- Install ffi by force if necessary


		gem install ffi -f



- Change your work set to where your github repository clone is (See the end of [last tutorial](https://uxxunet.github.io/2018/04/12/Blog-built-by-Jekyll-on-Github-Tutorial-for-amateur-1.html))and install github-page


		d:
		cd d:\Github\yourusername.github.io
		

- Create a file named "Gemfile" without any suffix(I use Notepad or Notepad++). Enter infomation blow and safe.


		source 'http://rubygems.org'
		gem 'github-pages', group: :jekyll_plugins
		gem 'wdm', '>= 0.1.0' if Gem.win_platform?

- Install bundle

		bundle install


- Update it if necessary


		bundle update


- Final command to generate your static blog page

 
		bundle exec jekyll serve


- In fact, there are many forms of this commands:


		jekyll s
		jekyll serve
		jekyll server
		bundle exec jekyll s
		bundle exec jekyll serve
		bundle exec jekyll server


They're not exactly the same.

Now, you can enter `127.0.0.1:4000` into your browser address bar to check your blog locally .


![1-11](http://p720v2ufu.bkt.clouddn.com/github/blog/1-11.png)

## Push your blogs online

- Install [git](https://git-scm.com/download/win)
- Open **git bush** and a little settings.
- Change your work set to where your github repository clone is and push it to the github.


		$ cd d:\
		$ cd d:\Github\yourusername.github.io
		$ git add .   # or git a
		$ git commit -m "updated site"
		$ git push -u origin master


- Also, you can operate the web locally to check the comtemporary web page(the same with **command prompt**):


		$ bundle exec jekyll serve


Enter `127.0.0.1:4000` into your browser address bar.


Now that you have the local repository and the tools to operate, you can try to change files locally.

Here comes the last step: write your own blog!

- Download **MarkdownPad 2** and start to blog. Just save all the .md blog in the folder _post.

Markdown is the blog style used in this blog. Mardown edit softwares are listed:
Window: MarkdownPad, MarkPad
ISO: Mou, Drafts, Day One, iA Writer,Tublme 
Oline: Draftin, Markable.in, Dillinger.io, MaDe(Chrome plugin)

How about "Hello World!"


![1-7](http://p720v2ufu.bkt.clouddn.com/github/blog/1-7.png)


About the syntax of markdown, here recommamd [the original one](https://daringfireball.net/projects/markdown/syntax), and [Chinese version](http://wowubuntu.com/markdown/#list)

After every changes in your blog, operate bundle `exec jekyll serve` and git push as described above or use GitHub DeskTop to push. Then, enter `yourusername.github.io` into your browser address bar and see what happens!


## Problemshooting

Once again, when encountering any problems, you can turn to me or google. Here is some warm-hearted blogers I found, who gave instructions of some problems.


- [moonclearner](https://blog.csdn.net/moonclearner/article/details/52238033)
- [Jekyll+Github个人博客构建之路](http://robotkang.cc/2017/03/HowToCreateBlog/)
- [Jekyll搭建个人博客](http://baixin.io/2016/10/jekyll_tutorials1/)


Thanks for reading! 

Any questions are welcome. I'm a starter myself so feel free to ask!


## Refference
- [Setting-up-your-github-pages-site-locally-with-jekyll](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)
- [Jekyll official documentation (English)](https://jekyllrb.com/docs/windows/)
- [Jekyll official documentation (Chinese)](http://jekyllcn.com/docs/windows/#installation)
- [Jens Willmer](https://jwillmer.de/blog/tutorial/how-to-install-jekyll-and-pages-gem-on-windows-10-x46)
- [JuLian Thilo](http://jekyll-windows.juthilo.com/)
- [Jekyll+Github个人博客构建之路](http://robotkang.cc/2017/03/HowToCreateBlog/)
- [Jekyll搭建个人博客](http://baixin.io/2016/10/jekyll_tutorials1/)
