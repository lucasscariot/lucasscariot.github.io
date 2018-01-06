---
layout: post
title: Generate a list of passwords with Crunch
date: 2016-03-18 23:19 +0100
categories: technical
---
Crunch is a word list generator with which it is possible to specify a standard character set and a number of characters.

## Installation

[Download from Sourceforge](https://sourceforge.net/projects/crunch-wordlist/files/crunch-wordlist) or with wget from your terminal :

{% highlight shell %}
  wget 'https://netcologne.dl.sourceforge.net/project/crunch-wordlist/crunch-wordlist/crunch-3.6.tgz'
{% endhighlight %}

Unpack the folder:
{% highlight shell %}
  tar -xvf crunch-3.6.tgz`
{% endhighlight %}

In the directory:
{% highlight shell %}
  cd crunch-3.6
{% endhighlight %}

Compile the code: (make sure you have gcc installed)
{% highlight shell %}
  make
{% endhighlight %}

Launch the software :
{% highlight shell %}
  ./crunch
{% endhighlight %}

## How to use it
Generate a list of combinations between 2 and 4 characters:
{% highlight shell %}
  ./crunch 2 4
{% endhighlight %}

Define characters they must be placed following the command :
{% highlight shell %}
  ./crunch 2 4 0123456789
{% endhighlight %}

Save combinations to a file :
{% highlight shell %}
  ./crunch 2 4 0123456789 > password.txt
{% endhighlight %}
