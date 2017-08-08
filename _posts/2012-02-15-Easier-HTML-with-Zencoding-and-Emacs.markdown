---
layout: post
title:  Easier HTML with zencoding-mode & Emacs
categories: [Emacs, Tips]
last_changed: 2017-08-08
meta_desc: An introduction to using zencoding-mode to simplify writing HTML in Emacs.
permalink: /2012/02/15/Easier-HTML-with-Zencoding-and-Emacs.html
---

I've always found writing HTML outlines a bit tedious, with HTML being a somewhat verbose and repetitive language. Then I found out about zencoding-mode for Emacs.

zencoding-mode is a minor-mode for Emacs which allows you to declare HTML elements in css-like syntax and expands your entries into HTML. I find this mode makes writing HTML outlines much less tedious.

For example, if you were to write the following...

{% highlight css %}
a#someid.site-link
{% endhighlight %}

and press `C-j` (bound to zencoding-expand-line) over this text, `zencoding-mode` will parse and translate this to an anchor ('a') element with and `id` of 'someid' and a `class` of 'site-link'. Note that the identifiers for id ('`#`') and class ('`.`') are the same as those you would use in css. The translated HTML would look something like this:

{% highlight html %}
<a id="someid" class="site-link"></a>
{% endhighlight %}

This example only scratches the surface of the cool things you can do with zencoding-mode. Using the same css-like syntax and features like declaring parent > child element relationships, sibling elements and element multipliers allow you to quickly write nested HTML in a much more concise and less error prone manner:

{% highlight css %}
#outer.box>h1+p.box-text*2
{% endhighlight %}

becomes: 

{% highlight html %}
<div id="outer" class="box">
    <h1></h1>
    <p class="box-text">
    </p>
    <p class="box-text">
    </p>
</div>
{% endhighlight %}

I won't go into much more detail about all the features of `zencoding-mode`, mostly because the project already has an excellent README document with plenty of examples. I will say that this library greatly changed the way I feel about having to write HTML.

You can get all the details about this project on the [zencoding project page](https://github.com/rooney/zencoding) on github.