---
layout: post
title:  How to create blog with Jekyll and host it on GitHub Pages
date:   2017-05-01 01:00:00 +0300
image: /assets/images/2017/jekyll.png
comments: true
tags:
- Manual
---

This manual provides an easy way to create static blog / personal page / other type of private site using [Jekyll](https://jekyllrb.com/) and [GitHub Pages](https://github.io).
Blog which you're reading right now is built exactly that way.

## Theme
Unlike other manuals, I recommend you to start with theme. Seriously, Google for 'Jekyll themes' and pick one that you like. Most of them have GitHub repos, so it should be easy to start. 

Okay, let's say you found a theme you like. Say it will be [hcz-jekyll-blog theme](https://github.com/codeasashu/hcz-jekyll-blog).
Theme demo can be found at [https://codeasashu.github.io/hcz-jekyll-blog/](https://codeasashu.github.io/hcz-jekyll-blog/)
Go to console, checkout theme:

    cd; mkdir theme; cd theme
    git clone https://github.com/codeasashu/hcz-jekyll-blog

Just in case, my blog uses [jekyll-theme-materialize](https://github.com/KeJunMao/jekyll-theme-materialize).

## Jekyll installation
It's quite simple. Just execute:

    gem install jekyll

Nothing more to say. However, there is a [detailed instruction](https://jekyllrb.com/docs/installation/).

## Repository
Now you need an account on the [GitHub](https://github.com). Create it if you don't have one. Next step is a repo. GitHub Pages requires you to have repo named your_username.github.io. So, create one with that name. [Here](https://pages.github.com/) is an instruction how to do that.

Now we need to checkout it. I recommend using SSH way to checkout to avoid problems in future. It should look like:

    cd; mkdir blog; cd blog
    git clone git@github.com:your_username/your_username.github.io.git

## Content
Now we need to move theme to our repo. Perform:

    mv ~/theme/hcz-jekyll-blog ~/blog/your_username.github.io/
    
Now you can start a local version of your blog! Do:

    cd ~/blog/your_username.github.io/
    jekyll serve
    
Site should be available by URL [http://127.0.0.1:4000/](http://127.0.0.1:4000/).

Open new console tab since existing one is busy with webserver. Fill _config.yml file with your info. If you are not sure what to fill, just leave fields empty - I did that for fields like 'cdnurl:' and 'google_analytics:'. Now cd to _posts directory and add some posts. If you already have a blog, there's a bunch of blog ]migration instructions](https://jekyllrb.com/docs/migrations/). You can easily switch from Blogger, Wordpress, etc. If no, just create a new post by adding new .markdown file. There's already several example posts, so it's easy to understand .markdown file syntax.

Also I strongly recommend to add '_site/' string to .gitignore file to avoid duplications on every change and save space on GitHub.

## Committing changes
If you have basic understanding of GIT then point is easy: commit and push  your changes. If not, there's a simple command to push changes:

    add -A; commit -m "CHANGES_DESCRIPTION"; git pull --rebase; git push

Replace CHANGES_DESCRIPTION with meaningful description of your changes - like 'Added new post'.

If you observe an issue during push then you may need to add SSH keys to your GitHub account See [how to do that](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).

That's it! Wait for a minute after commit to let GitHub do some magic. Then open [your_username.github.io](http://your_username.github.io).

## Domain
Optional step is a domain. If you don't like your_username.github.io as your site URL then you may create your own domain name for it. Steps are:
- Go to domain registrar which you like, say it will be [name.com](https://name.com);
- Search for a name, ensure it's free and not too expensive for you;
- Register your domain (just domain, we don't need hosting);
- Next step is not obvious - go to 'Websites' -> 'Apps' section of name.com and scroll for 'GitHub' there. Press 'Get started', select your domain and follow instructions;
- Almost done! The last step is to connect GitHub to your domain name. Go to Settings of your .github.io repo, scroll to 'Custom domain' section and enter your hostname;
- You may need to wait for a while (1-2 hours) or manually rebuild DNS cache to make it work;
- Enjoy your blog!
