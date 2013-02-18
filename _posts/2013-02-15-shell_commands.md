---
layout: post
title: Some shell commands | Ellioh Thot'o
header-title: Some shell commands
published: true  

tags: 
- shell
- command-line
- linux
---

1. Repeat previous command
{% highlight bash %}
!!
{% endhighlight %}

2. Copy a directory with scp
{% highlight bash %}
scp -r user@server:/path/directory .
{% endhighlight %}

3. Display memory use under the current directory
{% highlight bash %}
du -h -d 2
{% endhighlight %}

4. Open a file directly from a SVN server
{% highlight bash %}
svn cat svn://svn_server/project/branches/path/file|less
{% endhighlight %}

5. Open a previous version of a file without doing 'svn update' or 'svn checkout'
{% highlight bash %}
svn cat -r r49441 working_dir/path/file
{% endhighlight %}

6. Svn log get revisions by date : below we retrieve revision of 15th Feb 13
{% highlight bash %}
svn log --revision {2013-02-15}:{2013-02-16}|less
{% endhighlight %}

7. Use grep --exclude. For example, exclude svn hidden directory. 
{% highlight bash %}
 grep  searchedterm . -nR --exclude="*\.svn*"  2>/dev/null
{% endhighlight %}

7. Open a file returned by grep. We use the option '-l' to "clean" the path.
{% highlight bash %}
grep  checkStep1 . -lR  2>/dev/null|xargs vim -o
{% endhighlight %}