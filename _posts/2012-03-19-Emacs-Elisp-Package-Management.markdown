---
layout: post
title: Emacs Elisp Package Management, Finally!
category: Emacs
last_changed: 2012-03-19
meta_desc: Emacs 24 to include package.el and ELPA support for simpler Elisp package management.
permalink: /Emacs/2012/03/19/Emacs-Elisp-Package-Management.html
---

One of the many great things about using Emacs is the giant user
community and the diverse and comprehensive 3rd party packages &
libraries available. Unfortunately, there are so many
resources for these 3rd party packages that trying to quickly find
what you need can sometimes be a bit of an ordeal. Even given a great
resource like emacswiki.org, it's sometimes not clear what the most
current or definitive source for a certain software may be.

There have been several attempts at collecting and organizing this
code in the past, the most prominent being ELPA (Emacs Lisp Package
Archive) which is not only an archive of emacs lisp packages, but also
provides `package.el`, an emacs lisp package manager which is used to
install and manage emacs lisp packages available in the ELPA.
 
package.el is certainly not the only package archive/manager available for
Emacs, but it does seem to have the most traction, and more
importantly, will be included by default starting with Emacs 24!

Starting with Emacs 24, you can list available packages by
simply typing `M-X list-packages`. From this new buffer you can now select
to view package details, install, update and remove packages.

![Emacs list-packages example
 buffer](/images/emacs_list-packages_example.png "Emacs list-packages example")

Try `C-h f package-menu-mode` for more information.

It's also worth noting that the emacs version of `package.el` allows
multiple repositories which allows you to add compatible package archives
in addition to the GNU ELPA by editing the `package-archives` variable. It's 
also worth mentioning that the GNU ELPA archive (http://elpa.gnu.org) is 
not the same as the original ELPA archive (http://tromey.com/elpa/). It's 
not clear to me whether these archives will be synchronized at some point 
 or continue to be maintained as separate projects.

Easy Emacs lisp package management, finally.

If you can't wait for the Emacs 24.1 release, you can install
package.el from the [ELPA homepage](http://tromey.com/elpa/ "ELPA"). Or, if 
you're more adventurous, build Emacs 24 yourself from 
[source](http://savannah.gnu.org/projects/emacs/).

External Links:

* [GNU Emacs Lisp Package Archive](http://elpa.gnu.org/packages/) 
* [ELPA](http://tromey.com/elpa/ "ELPA") 
* [Marmalade package archive](http://marmalade-repo.org/ "Marmalade") 3rd party package archive compatible with package.el