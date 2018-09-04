---
layout: post
title: Execute promises sequentially in javascript
date: 2018-09-04 22:13 +0200
---
This week in a project, I had an array of promises I needed to execute one by one.

Instead of usual `Promise.all`, I installed [Bluebird](http://bluebirdjs.com) and used `Promise.map`.

Initial code executing simultaneously:
{% highlight javascript %}
const someFunction = async () => {
  const userIds = [1, 2, 3, 4]

  try {
    await Promise.all(userIds.map(async userId => updateUser(userId)))
  } catch (error) {
    console.error(error)
  }
}
{% endhighlight %}

Code with bluebird executing promises sequentially 

{% highlight javascript %}
const someFunction = async () => {
  const userIds = [1, 2, 3, 4]

  try {
    await Promise.map(userIds, userId => updateUser(userId, 0), {
      concurrency: 1,
    })
  } catch (error) {
    console.log(error)
  }
}
{% endhighlight %}

[Bluebird - Promise.map](http://bluebirdjs.com/docs/api/promise.map.html)