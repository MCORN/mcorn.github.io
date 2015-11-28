---
title: Creating this jekyll site
updated: 2015-11-28 22:43
---

# Setting up jekyll on Ubuntu 12.04

## Upgrade stock ruby to ruby 2.0
`sudo apt-add-repository ppa:brightbox/ruby-ng-experimental` 
`sudo apt-get update`
`sudo apt-get install -y ruby2.0 ruby2.0-dev ruby2.0-doc`

[source](http://stackoverflow.com/questions/18490591/how-to-install-ruby-2-on-ubuntu-without-rvm)

## Set up the defaults to ruby 2.0
`sudo update-alternatives --config ruby`
`sudo update-alternatives --config gem`

[source](https://leonard.io/blog/2012/05/installing-ruby-1-9-3-on-ubuntu-12-04-precise-pengolin/)

## Install Jekyll itself
`sudo gem install jekyll`

[source](http://www.hongkiat.com/blog/blog-with-jekyll/)

## Set up a Jekyll blog
Find a [theme](https://github.com/jekyll/jekyll/wiki/Themes), download it to your computer, cd into the folder and type
`jekyll serve --watch`
to see the site!
