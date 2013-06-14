---
title: Create a custom authentication decorator in Django
author: Dan
layout: post
permalink: /2012/07/create-a-custom-authentication-decorator-in-django/
categories:
  - Article
tags:
  - authentication
  - decorators
  - django
  - programming
  - python
  - web
---
Django leverages Python&#8217;s ability to use decorators extensively. Decorators in Python are defined as:

> A Python decorator is a specific change to the Python syntax that allows us to more conveniently alter functions and methods.

In layman&#8217;s terms, decorators allow us to dynamically alter functions without having to actually change the function itself. Sounds pretty neat? Well, you can read more about Python Decorators [here][1] and [here][2].

The most common use of a decorator is the infamous [login_required][3]. This decorator is used in conjunction with a **view** that restricts access to authenticated users only. 

<pre class="brush: python; title: ; notranslate" title="">from django.contrib.auth.decorators import login_required
from django.shortcuts import render

@login_required
def my_view(request):
    return render(request, 'template.html')
</pre>

This decorator is very useful, because I don&#8217;t have to actually change anything about my view to restrict access to it. However, what if you want to restrict a view to only authenticated users who are **currently active**? This can easily be accomplished with a custom decorator:



Thanks to the [user\_passes\_test][4] decorator that comes with Django, we can chain this together with the [login_required][3] to create our custom decorator. 

To break it down further, we pass an anonymous function into the user\_passes\_test decorator that returns the value of [is_active][5], which is a boolean that designates if the user is active. Next we set the **login_url** parameter, which will redirect to this URL if the user is **not** active. For further reference, check out the actual source for [user\_passes\_test][6].

Now we just update our view to incorporate our new, reusable **decorator.py** package and decorator.

<pre class="brush: python; title: ; notranslate" title="">from django.shortcuts import render

from myapp.decorators import active_and_login_required

@active_and_login_required
def my_view(request):
    return render(request, 'template.html')
</pre>

 [1]: http://wiki.python.org/moin/PythonDecorators
 [2]: http://stackoverflow.com/questions/739654/understanding-python-decorators
 [3]: https://docs.djangoproject.com/en/1.3//topics/auth/#the-login-required-decorator
 [4]: https://docs.djangoproject.com/en/dev/topics/auth/#limiting-access-to-logged-in-users-that-pass-a-test
 [5]: https://docs.djangoproject.com/en/dev/topics/auth/#fields
 [6]: https://github.com/django/django/blob/master/django/contrib/auth/decorators.py