---
layout: post
title: Delete keys in redis with command line
date: 2018-01-18 10:53 +0100
---
Make sure you have `redis-cli` installed in your computer.

If your on a OSX, simply run `brew install redis`.

## List keys
#### All keys
First, list all the keys present in the database.

Without precision, the default database used by `redis-cli` is db 0.
{% highlight shell %}
  redis-cli --raw keys '*'
{% endhighlight %}

To specify a database number user the parameter `-n`
{% highlight shell %}
  redis-cli -n 3 --raw keys '*'
{% endhighlight %}

#### Search a specific pattern
{% highlight shell %}
  redis-cli --raw keys '/user/*'
{% endhighlight %}

#### Remove keys
{% highlight shell %}
  redis-cli --raw keys '/user/*' | xargs redis-cli DEL
{% endhighlight %}

## With Parameters
#### Redis URI
To prevent writing twice the uri i create a variable.
{% highlight shell %}
  REDIS_URI='redis://..'
  redis-cli -u $REDIS_URI --raw keys '/user/*' | xargs redis-cli -u $REDIS_URI DEL
{% endhighlight %}

#### Redis db number
{% highlight shell %}
  redis-cli -n 3 --raw keys '/user/*' | xargs redis-cli -n 3 DEL
{% endhighlight %}
