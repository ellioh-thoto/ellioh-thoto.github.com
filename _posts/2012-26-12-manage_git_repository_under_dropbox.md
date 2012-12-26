--- 
layout: post
title: My Git Memo 
published: true  

tags: 
- Git 
- Versionning
---

Why?
----

I was search for a solution to get private repositories for my personal project. 
Github is fine for that but private repositories in Github is not free. So I concluded Github was not fine enough :).
After some "googlisement", I found "Bitbucker" as the saver, better I found "Dropbox"! What's pretty sweet idea!

Actually, I was searching for the free and easy to access repository, easy to share with a community, Dropbox made
repository as easy to reach as a local directory. In addition, no ssh public is no needed anymore! It is as sweet as that

How?
----

###1. Dropbox###

You must first have a Dropbox account and install the application on your computer. Once you have you Dropbox directory
synchronized, you can considere you "git server" is ready for the job.

###2. The repository###

Then create the git repository. On Windows (sometimes we can't choice to be free... :'( ) you can use a Git+. This cool application provides
a unix-like terminal powerded by Cygwin tool.

{% highlight bash %}
cd ~/Dropbox
mkdir myrepo.git
cd !$
git --bare init
{% endhighlight %}

###3. Share the repository with you coworkers (Optionnal)###

Go to your Dropbox directory in the explorer. Right clicks on the repository folder : Dropbox > Share the folder.
Then enter the mail of the persons you want to add to share you repository with.

Notice : the entered mail addresses must be the same addresses used by your co-workers to create there dropbox account.


###4. Working directory###
- Create a working directory

{% highlight bash %}
cd ~/Projects/myrepo # or go to you project directory
git init
git remote add origin ~/Dropbox/myrepo.git
touch test.txt
git add test.txt
git commit test.txt -m 'Initial commit'
git push origin master
{% endhighlight %}

- Clone from an existing directory

The repository should have been already shared with you though Dropbox.

{% highlight bash %}
git clone ~/Dropbox/myrepo.git 
{% endhighlight %}

That's it! No more git user to use anymore, no more privileges to carry on, Git and Dropbox made it possible! :)


Reference
---------
[http://tumblr.intranation.com/post/766290743/using-dropbox-git-repository](http://tumblr.intranation.com/post/766290743/using-dropbox-git-repository)
[http://gitref.org/](http://gitref.org/)
[https://www.dropbox.com/help/19/en](https://www.dropbox.com/help/19/en)
