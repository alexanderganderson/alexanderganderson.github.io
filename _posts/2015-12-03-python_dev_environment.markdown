---
layout: post
title: Python Environment for Computational Neuroscience
---

By reading this post, you will learn about all to the tools that I have found
to be useful as a graduate student in computational neuroscience.
Note that I do my coding on an OSX based machine.

# Terminal

For most coding purposes, it is important to get comfortable with the terminal.
The main commands that I have found to be useful are `ls, cd, clear, mv`. Also it is important to understand the way files are structured and what is in your `~/.bash_profile`. Googling these things will give the answers. 

# Python Installation

The easiest method to install python is to use anaconda python distribution.
See here for more details [anaconda]. 

# Git

One of the most important things to do when programming is to manage 
the versions of your files carefully. I strongly recommend making a 
github account, and reading the first two chapters of [git-handbook] to 
understand how it works.

# Basic Text Editors

Lots of people have strong opinions about their favorite text editor.
Here is what I've settled on. I use both emacs and vim depending on the
situation. I have also found it quite helpful to remap my control key 
to the caps lock key. I have found that some of the emacs commands are
super useful (and generalize to a lot of other editors) such as CTRL-E
that takes you to the end of a line. However, I found that I prefer
the vim commands as you don't need the META key. 

Beyond those basic editors, I also played around with a few more 
sophisticated editors. 

# More Sophisticated Editors

Currently, I am using Sublime Text 3 as my main python editor when I am
making more substantial changes to my code. It has a great system for 
installing add-ons. The following website has some good info on
configuring SB3 for python development. In short, I use Package Control,
a different theme, sidebar enhancements, anaconda, SublimeLinter, and
GitGutter. 

# Code Linting

One way to speed up python development is to use a code linter, or a 
program that goes through your code and checks for various errors. 
The anaconda addition to SB3 has a linter that I disabled, but I use the
flake8 code linter. This linter is a combination of the pep8 and pyflakes. 
These linters catch a reasonable number of errors and help you format
your code so that it is easy for others to read.  

# Code Visualization

As far as running python code is concerned, I have found it to be useful to
use a combination of running scripts from the terminal and ipython notebook.
Ipython notebook allows you to interactively run different parts of your
code without restarting the script. I have found that it has been good to
prototype my code and visualize the results with ipython notebook while
the main code is executed using a script.

# Working on Remote Computers

As a lot of my research involves intensive computation, I often connect up to
other computers. The first key thing to use is `ssh` with the name of your
server. You can either enter a password or use a ssh key. See here for more 
info: [ssh-gen]. Another neat trick is that you can use ipython notebook
on a remote computer by doing the following:
SSH with port forwarding:

`ssh -L 8888:localhost:8888`

Then start an ipython notebook looking at that port on your computer:

`ipython notebook --port < portnumber>`

# Running Long Jobs on a Remote Machine

When you log out of a remote machine, it can end your session. The tool that
I currently use is screen. The idea is that I can open up a session of
screen, run my code from there, log out, come back, and my script is still
running. 

[anaconda]: http://docs.continuum.io/anaconda/install
[git-handbook]: https://git-scm.com/book/en/v2
[st3-config]: https://realpython.com/blog/python/setting-up-sublime-text-3-for-full-stack-python-development/
[ssh-gen]: https://help.github.com/articles/generating-ssh-keys/
 