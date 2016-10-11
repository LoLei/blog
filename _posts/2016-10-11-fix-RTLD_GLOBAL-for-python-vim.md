---
layout: post
title: How to fix the RTLD_GLOBAL Vim compilation error
author: Lorenz Leitner
categories: Tutorials
---

If you want to compile Vim with Python 2 or 3 support, you may run into this 
error. I haven't found a precise solution online, so here is how I fixed it.

---

The error can occurr when you try to configure Vim compilation files with 
Python support, that is after you run `./configure` inside the Vim source 
directory with the enabled Python flags:

`checking whether we can do without RTLD_GLOBAL for Python... no`
`checking whether we can do without RTLD_GLOBAL for Python3... no"`

The worst thing is, this error just prints somwhere in the configuration
log, you have to grep for it to see it. The configuration still completes
and you can compile Vim afterwards, but the Python support doesn't work.


### Anyway, here's how to fix it
`sudo porg -lD 'make install'`

Run this after `make` or however you did the compilation.
The second command makes the magic happen. 
[Porg](https://aur.archlinux.org/packages/porg/) fixes the Python problems 
after the compilation.

Try `:echo has(python)` now, if it returns `1` you're good to go!
