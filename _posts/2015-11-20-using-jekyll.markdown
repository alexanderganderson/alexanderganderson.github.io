---
layout: post
title: "Using Jekyll"
date: 2015-11-20
categories: code
---

The goal of this post is to summarize how I got started using jekyll for static website creation. 
Jekyll hosted through github allows you to make a nice looking website
that is easy to maintain. 


# Installation

As a first step, go to [jekyll-quickstart]. Begin by installing the github version of jekyll by running:

`gem install github-pages`

This installs the version of jekyll used by github to build your website. 

# Creating your first page

Create a directory for your website on your computer. The quickstart guide suggests
running the code `jekyll new myblog` to generate a site template in the directory
`myblog`. After looking at that, the best way to get going quickly is to clone an 
existing jekyll template (eg. look here: [jekyll-themes]) and modify the template
to your needs.

# Viewing changes to your page 

You can check the website by going into the directory and typing
`jekyll serve`

This hosts the website on your computer and allows you to repeatedly modify your website and view the changes. 

# Notes


Note that jekyll build creates a directory `_site` that takes all of the pages that you've written in markdown and generates the actual html.
You don't need to do this for github, as it builds your site (and you want your .gitignore to have the `_site` folder). 

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
[jekyll-themes]: http://jekyllthemes.org/
