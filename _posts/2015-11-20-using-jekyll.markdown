---
layout: post
title: "Using Jekyll"
date: 2015-11-20
categories: code
---

The goal of this post is to summarize how I got started using jekyll for static website creation. 

The reason for using Jekyll is that it creates an easy to maintain 
static website that can be hosted on github. That way, you don't need to 
constantly worry about updating your website. 


# Installation

As a first step, go to [jekyll-quickstart]. Here, you create a jekyll directory.

Roughly, the steps are:

Install jekyll and specifically github-pages by running 

`gem install github-pages`

# Creating your first page

Create a directory for your website on your computer. 
You can do this by forking an existing jekyll template (try looking for one on google). 

You can check the website by going into the directory and typing
`jekyll serve`

This hosts the website on your computer and allows you to repeatedly modify your website and view the changes. 

# Notes



Note that jekyll build creates a directory _site that takes all of the pages that you've written in markdown and generates the actual html.
You don't need to do this for github, as it builds your site (and you want your .gitignore to have the _site folder). 

# Hosting

Create your github repo for your website. Eg. follow step one here [github-pages]. 

Initialize the folder with your website as a git-repo and push your website to git. 

# Modifying your website

By looking at examples (such as this site!) you can see how people manipulate the 
basic tools included in jekyll. The most useful feature that I've found is that
you can create a data file and then parse that data with a for loop to generate
a good looking table. 


[jekyll-quickstart]: http://jekyllrb.com/docs/quickstart/
[github-pages]: https://pages.github.com/