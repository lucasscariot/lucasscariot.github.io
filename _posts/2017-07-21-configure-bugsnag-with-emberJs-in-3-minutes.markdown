---
layout: post
title: "Configure Bugsnag with EmberJs in 3 minutes"
date: 2017-07-21 22:58:36 +0100
categories: technical
---
Bug tracking is important to maintain a healthy front app.
If you use EmberJs here is how to configure bugsnag to track your bugs.

## Installation
{% highlight shell %}
  bower install bugsnag --save
{% endhighlight %}

*Brocfile.js*
{% highlight javascript %}
  // Error tracking with Bugsnag
  app.import('bower_components/bugsnag/src/bugsnag.js');
{% endhighlight %}

*config/environment.js*
{% highlight javascript %}
  'BUGSNAG': {
    key: process.env.BUGSNAG_API_KEY
  }
{% endhighlight %}

*instance-initializers/bugsnag.js*

{% highlight javascript %}
'use strict';
import Ember from 'ember';
import config from '../config/environment';

export default {
  name: 'bugsnag',

  initialize: function(appInstance) {
    const appController = appInstance.lookup('controller:application');

    Bugsnag.apiKey = config.BUGSNAG.key;
    Bugsnag.releaseStage = config.environment;
    Bugsnag.notifyReleaseStages = ['staging', 'production'];

    // Notify Routing Errors and edge cases
    Ember.onerror = function(error) {
      Bugsnag.context = appController.get('currentPath');
      Bugsnag.notifyException(error);
      console.error(error.stack);
    };

    // Notify Promises Errors
    Ember.RSVP.on('error', function (error) {
      Bugsnag.context = appController.get('currentPath');
      Bugsnag.notifyException(error);
    });

    // Notify Ember Logger Errors
    Ember.Logger.error = function (message, cause, stack) {
      Bugsnag.context = appController.get('currentPath');
      Bugsnag.notifyException(new Error(message), null, { cause: cause, stack: stack });
      console.error(stack);
    };
  }
};
{% endhighlight %}


## Linter || Eslint
*eslintrc.js*
{% highlight javascript %}
  globals: {
    "Bugsnag": true
  }
{% endhighlight %}

*.jshintrc*
{% highlight javascript %}
  "predef": {
    "Bugsnag": true
  }
{% endhighlight %}
