---
layout: post
title: Basic Raspberry Configuration
date: 2017-07-30 23:31 +0100
categories: technical
---
## Linux update
Let's begin with the classic updates of linux.
{% highlight shell %}
  sudo apt-get update
  sudo apt-get upgrade
  sudo reboot
{% endhighlight %}

## Raspberry configuration
A command allows access to the options of the raspberry, for example the startup, the ssh, overclocking.

{% highlight shell %}
  raspi-config
{% endhighlight %}

With this configuration, I activate the ssh, and disable the GUI at startup.

## Setup the wifi
Be sure to have your packages updated :

{% highlight shell %}
  sudo rpi-update
  sudo reboot
{% endhighlight %}

Wicd can help, it's a graphical wireless and wired connection manager.
{% highlight shell %}
  sudo apt-get install wicd
{% endhighlight %}

Scan the networks :
{% highlight shell %}
  wpa_cli scan && sleep 5 && wpa_cli scan_results
{% endhighlight %}

Once your SSID has been found, you must modify this file:

{% highlight shell %}
  sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
{% endhighlight %}
