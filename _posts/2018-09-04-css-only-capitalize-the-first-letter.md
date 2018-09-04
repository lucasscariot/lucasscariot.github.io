---
layout: post
title: CSS - Only capitalize the first letter
date: 2018-08-30 21:51 +0200
---

Here is a small CSS trick that can be useful.

Sometimes the `text-transform: capitalize;` isn't what we need. Because it converts the first letter **of each word** to uppercase.

[Mozilla Documentation - text-transform CSS Property](https://developer.mozilla.org/en-US/docs/Web/CSS/text-transform)

So, for this sentence:

{% highlight text %}
hello world!
{% endhighlight %}

The result will be:

{% highlight text %}
Hello World!
{% endhighlight %}

There is a CSS [pseudo-element](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements) that allow you to customize the first letter of a selector.

{% highlight css %}
p::first-letter {
text-transform: uppercase;
}
{% endhighlight %}

[Mozilla Documentation ::first-letter](https://developer.mozilla.org/en-US/docs/Web/CSS/::first-letter)

Here is the result for the same sentence with this pseudo element:
{% highlight text %}
Hello world!
{% endhighlight %}
