---
title       : Python 2 vs. Python 3
subtitle    : 
author      : Leslie Emery
job         : Genetic Analysis Center
framework   : deckjs        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : solarized_light
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

# Python 2 vs. Python 3
GAC coding dicussion  
October 11, 2017  

---
# History
Why are there two versions of Python?  

---
## Short answer: Guido wanted a new version

> Guido van Rossum (the original creator of the Python language) decided to clean up Python 2.x properly, with less regard for backwards compatibility than is the case for new releases in the 2.x range.  

* Python 3.0 was released in 2008, with lots of major improvements, but not backwards-compatible
* Python 2.7 has been maintained ever since as an "end of life" release to support existing code
    * Some 3.x features have been backported to 2.7
    * 2.6 was the last release before 3.0 came out; 2.7 was released in 2010 to ease the transition
    * Loses support in **2020**
    * Current support is only for bugs and security fixes (no more backporting)

---
# How do I decide which version to use?  

---
# 
> Python 2.x is legacy, Python 3.x is the present and future of the language.  

* [Wiki.python.org](https://wiki.python.org/moin/Python2orPython3)

---
## You should usually use 3.x unless you have a good reason not to
* 2008: lots of effort, few libraries, little awareness
* 2012: some effort, some libraries, some awareness, major debate
* 2017: some effort, most libraries, major awareness, debate is over

* For an alternative perspective: [Python 3 is killing Python](http://blog.thezerobit.com/2014/05/25/python-3-is-killing-python.html)

---
## Use Python 3.x when ...
* ... you never learned 2.7 anyway
* ... you're writing a major new project
* ... an important library requires 3.x (e.g. Django)

---
## Use Python 2.7 when ...
* ... an important library is still in 2.7
* ... you're working with legacy code
* ... you don't have time to learn changes for 3.0
    * (these changes are easy to adjust to, but you may not have the time/focus to do so)
* ... you're deploying to an environment you don't control (e.g. a server or cluster where only 2.7 is available)

---
## Current Python 3 library support

### 6,000 stable and actively developed packages on PyPI
![](https://cdn-images-1.medium.com/max/1600/1*dfZp1DzXw4oGnUvMff100A.png)

### The 28% of packages that are Python 2 only
![](https://cdn-images-1.medium.com/max/1600/1*LBjOKMUe1eXygimuyNudhQ.png)

### Current status of 360 most popular PyPI packages
[Python 3 Readiness](http://py3readiness.org/)

---
## High adoption rates among data scientists in 2016

![Work python version](http://ianozsvald.com/wp-content/uploads/2016/06/work_python.png)
![Non-work python version](http://ianozsvald.com/wp-content/uploads/2016/06/home_python.png)
![Expecting to switch soon?](http://ianozsvald.com/wp-content/uploads/2016/06/upgrading.png)
![Version used most?](http://ianozsvald.com/wp-content/uploads/2016/06/distribution.png)

---
# Using both versions of Python
Most systems currently maintain python 2.7 and python 3.x simultaneously

---
## On the compute clusters

```
03:34 PM emeryl@fisher ~ $ which python
/usr/bin/python
03:34 PM emeryl@fisher ~ $ which python2
/usr/bin/python2
03:34 PM emeryl@fisher ~ $ which python3
/usr/local/bin/python3
03:34 PM emeryl@fisher ~ $ ls -lhA /usr/local/bin/python*
lrwxrwxrwx 1 root root 35 Sep 10  2012 /usr/local/bin/python2.7 -> /usr/local/python-2.7/bin/python2.7
lrwxrwxrwx 1 root root 42 Sep 10  2012 /usr/local/bin/python2.7-config -> /usr/local/python-2.7/bin/python2.7-config
lrwxrwxrwx 1 root root  9 Sep 11  2012 /usr/local/bin/python3 -> python3.1
lrwxrwxrwx 1 root root 37 Sep 11  2012 /usr/local/bin/python3.1 -> /usr/local/python-3.1.2/bin/python3.1
lrwxrwxrwx 1 root root 44 Sep 11  2012 /usr/local/bin/python3.1-config -> /usr/local/python-3.1.2/bin/python3.1-config
lrwxrwxrwx 1 root root 35 Jan  4  2016 /usr/local/bin/python3.4 -> /usr/local/python-3.4/bin/python3.4
lrwxrwxrwx 1 root root 36 Jan  4  2016 /usr/local/bin/python3.4m -> /usr/local/python-3.4/bin/python3.4m
lrwxrwxrwx 1 root root 43 Jan  4  2016 /usr/local/bin/python3.4m-config -> /usr/local/python-3.4/bin/python3.4m-config
03:35 PM emeryl@fisher ~ $ ls -lhA /usr/bin/python*
-rwxr-xr-x 2 root root 8.9K May 22  2015 /usr/bin/python
lrwxrwxrwx 1 root root    6 Jun 29  2016 /usr/bin/python2 -> python
-rwxr-xr-x 2 root root 8.9K May 22  2015 /usr/bin/python2.6
-rwxr-xr-x 1 root root 1.4K May 22  2015 /usr/bin/python2.6-config
lrwxrwxrwx 1 root root   16 Jun 29  2016 /usr/bin/python-config -> python2.6-config
```

---
## On your desktop

### On a Mac

* Apple's python  

```
01:00 PM emeryl@gcc-mac-004 ~ $ /usr/bin/python2.6
Python 2.6.9 (unknown, Feb  7 2017, 00:08:08) 
[GCC 4.2.1 Compatible Apple LLVM 8.0.0 (clang-800.0.34)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 
  
```

* MacPorts  

```
12:58 PM emeryl@gcc-mac-004 ~ $ port select --summary
Name        Selected      Options
====        ========      =======
mysql       mysql57       mysql57 none
pip         pip34         none
python      python34      python26-apple python27 python27-apple python34 python35 none
python2     python27      python26-apple python27 python27-apple none
python3     python34      python34 python35 none
virtualenv  virtualenv34  virtualenv34 virtualenv35 none

12:58 PM emeryl@gcc-mac-004 ~ $ which python
/Users/emeryl/macports/bin/python
12:59 PM emeryl@gcc-mac-004 ~ $ which python2
/Users/emeryl/macports/bin/python2

12:59 PM emeryl@gcc-mac-004 ~ $ ls -lhA ~/macports/bin/python*
lrwxr-xr-x  1 emeryl  staff    36B Jun 29 17:29 /Users/emeryl/macports/bin/python -> /Users/emeryl/macports/bin/python3.4
lrwxr-xr-x  1 emeryl  staff    43B Jun 29 17:29 /Users/emeryl/macports/bin/python-config -> /Users/emeryl/macports/bin/python3.4-config
lrwxr-xr-x  1 emeryl  staff    18B Oct 11 12:59 /Users/emeryl/macports/bin/python2 -> /usr/bin/python2.6
lrwxr-xr-x  1 emeryl  staff    25B Oct 11 12:59 /Users/emeryl/macports/bin/python2-config -> /usr/bin/python2.6-config
lrwxr-xr-x  1 emeryl  staff    85B Sep 27 09:57 /Users/emeryl/macports/bin/python2.7 -> /Users/emeryl/macports/Library/Frameworks/Python.framework/Versions/2.7/bin/python2.7
lrwxr-xr-x  1 emeryl  staff    92B Sep 27 09:57 /Users/emeryl/macports/bin/python2.7-config -> /Users/emeryl/macports/Library/Frameworks/Python.framework/Versions/2.7/bin/python2.7-config
lrwxr-xr-x  1 emeryl  staff    36B Sep 28 11:03 /Users/emeryl/macports/bin/python3 -> /Users/emeryl/macports/bin/python3.4
lrwxr-xr-x  1 emeryl  staff    43B Sep 28 11:03 /Users/emeryl/macports/bin/python3-config -> /Users/emeryl/macports/bin/python3.4-config
lrwxr-xr-x  1 emeryl  staff    85B Sep 27 15:23 /Users/emeryl/macports/bin/python3.4 -> /Users/emeryl/macports/Library/Frameworks/Python.framework/Versions/3.4/bin/python3.4
lrwxr-xr-x  1 emeryl  staff    92B Sep 27 15:23 /Users/emeryl/macports/bin/python3.4-config -> /Users/emeryl/macports/Library/Frameworks/Python.framework/Versions/3.4/bin/python3.4-config
lrwxr-xr-x  1 emeryl  staff    86B Sep 27 15:23 /Users/emeryl/macports/bin/python3.4m -> /Users/emeryl/macports/Library/Frameworks/Python.framework/Versions/3.4/bin/python3.4m
lrwxr-xr-x  1 emeryl  staff    93B Sep 27 15:23 /Users/emeryl/macports/bin/python3.4m-config -> /Users/emeryl/macports/Library/Frameworks/Python.framework/Versions/3.4/bin/python3.4m-config
lrwxr-xr-x  1 emeryl  staff    85B Sep 27 15:24 /Users/emeryl/macports/bin/python3.5 -> /Users/emeryl/macports/Library/Frameworks/Python.framework/Versions/3.5/bin/python3.5
lrwxr-xr-x  1 emeryl  staff    92B Sep 27 15:24 /Users/emeryl/macports/bin/python3.5-config -> /Users/emeryl/macports/Library/Frameworks/Python.framework/Versions/3.5/bin/python3.5-config
lrwxr-xr-x  1 emeryl  staff    86B Sep 27 15:24 /Users/emeryl/macports/bin/python3.5m -> /Users/emeryl/macports/Library/Frameworks/Python.framework/Versions/3.5/bin/python3.5m
lrwxr-xr-x  1 emeryl  staff    93B Sep 27 15:24 /Users/emeryl/macports/bin/python3.5m-config -> /Users/emeryl/macports/Library/Frameworks/Python.framework/Versions/3.5/bin/python3.5m-config
lrwxr-xr-x  1 emeryl  staff    37B Sep 28 11:03 /Users/emeryl/macports/bin/python3m -> /Users/emeryl/macports/bin/python3.4m
lrwxr-xr-x  1 emeryl  staff    44B Sep 28 11:03 /Users/emeryl/macports/bin/python3m-config -> /Users/emeryl/macports/bin/python3.4m-config
lrwxr-xr-x  1 emeryl  staff    19B Oct 11 12:59 /Users/emeryl/macports/bin/pythonw2 -> /usr/bin/pythonw2.6
lrwxr-xr-x  1 emeryl  staff    86B Sep 27 09:57 /Users/emeryl/macports/bin/pythonw2.7 -> /Users/emeryl/macports/Library/Frameworks/Python.framework/Versions/2.7/bin/pythonw2.7
```

* Homebrew

### Windows

Any suggestions?  

---
## Major differences between the versions
http://sebastianraschka.com/Articles/2014_python_2_3_key_diff.html

### Dictionary iterator methods are gone  

* `dict.iterkeys()`, `dict.itervalues()`, and `dict.iteritems()` are gone  
* These methods used to return iterator versions of the lists that were returned by `dict.keys()`, `dict.values()`, and `dict.items()`  
* Python 3 dicts return "dictionary views" from `dict.keys()`, `dict.values()`, and `dict.items()`, and these views are similar to iterators, so the iterator methods have been removed

---
## Converting code from 2.7 to 3.x
* Use the 2to3 conversion utility

> ...well-written 2.x code can be a lot like 3.x code.

---


## References

[Should I use Python 2 or Python 3 for my development activity?](https://wiki.python.org/moin/Python2orPython3)  
[What should I learn as a beginner: python 2 or python 3?](https://learntocodewith.me/programming/python/python-2-vs-python-3/)  
[The key differences between Python 2.7.x and Python 3.x with examples](http://sebastianraschka.com/Articles/2014_python_2_3_key_diff.html)  
[Python 2 vs Python 3: Practical Considerations](https://www.digitalocean.com/community/tutorials/python-2-vs-python-3-practical-considerations-2)  
[Python 3 vs Python 2: it’s different this time](https://www.activestate.com/blog/2017/01/python-3-vs-python-2-its-different-time)  
[Python 2 vs Python 3: Which to Learn?](https://wsvincent.com/python2-vs-python3/)  
[Python 3 in 2016](https://hynek.me/articles/python3-2016/)  
[Results for “Which version of Python (2.x vs 3.x) do London Data Scientists   use?”](http://ianozsvald.com/2016/06/20/results-for-which-version-of-python-2vs3-do-london-data-scientists-use/)
[Adopt Python 3](https://medium.com/broken-window/python-3-support-for-third-party-libraries-dcd7a156e5bd)  
[Python 2 or 3?](https://www.fullstackpython.com/python-2-or-3.html)  
[Python 3 Readiness](http://py3readiness.org/)  
[2013 usage survey](https://wiki.python.org/moin/2.x-vs-3.x-survey)  
