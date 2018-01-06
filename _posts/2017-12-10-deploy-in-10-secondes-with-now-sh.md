---
layout: post
title: Deploy in 10 secondes with now.sh
date: 2017-12-10 23:50 +0100
categories: technical
---
Now is  a service that allows you to deploy your code in 10 seconds.

It works for a static site (index.html), Node Js (index.js) and Docker!

## Installation
[now.sh/download](https://now.sh/download)

## Utilisation
Hello World with NodeJS and Micro.

#### Create a directory:
{% highlight shell %}
  mkdir helloworld
{% endhighlight %}

#### Create the app:
{% highlight shell %}
  npm init
{% endhighlight %}

#### Installing an HTTP Microservice:
{% highlight shell %}
 npm install micro --save
{% endhighlight %}

#### Display a Hello World:

*atom index.js*
{% highlight javascript %}
  const micro = require('micro')

  const server = micro(async (req, res) => {
    res.writeHead(200)
    res.end('Hello World !')
  })

  server.listen(80)
{% endhighlight %}
The application is over just run the command :
{% highlight shell %}
  now
{% endhighlight %}

[https://helloworld-gwklzargzj.now.sh](https://helloworld-gwklzargzj.now.sh)

*The service is free for 20 deployments per month with 1GB of bandwidth.*

- [zeit.co](https://zeit.co)
- [github.com/zeit](https://github.com/zeit)
