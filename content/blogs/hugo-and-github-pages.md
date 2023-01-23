---
title: "Creating a CV and Blog Website with Hugo and GitHub Pages"
date: 2023-01-05T20:53:58+05:30
draft: true
github_link: "https://github.com/mattgirdler"
author: "Matt"
tags:
  - Blog
image: /images/projects/profile.png
description: "How I created this site!"
toc: 
---

In the absence of inspiration, I thought what better way to christen this new blog than to explain how I made it!

## Background
I'll start off by talking a bit about why I created this blog, and why I chose Hugo with GitHub Pages. If that's not of interest to you, you can skip ahead to the main content.

### Domain
I've had this domain since 2009, when it was bought for me by a family member. I didn't know what to do with it at the time, and didn't really think about it until last year when the ownership was transferred over to me. 
This seemed like as good an excuse as any to try and tick off two tasks that had been on my personal backlog for a while:
- create a living CV (I hate dealing with Word docs) 
- start blogging

### Hugo
I came across Hugo during a work project while investigating a static site generator that could replace a WordPress website. I considered a few different options, including Jekyll and Gatsby, but Hugo seemed to be the most fuss-free of the bunch. 
It also has a number of options for exporting from WordPress, as well as some neat add ons like Netlify CMS for a tidy admin interface with a rich text editor - because most people really don't want to deal with markdown. I might implement that on this site if the markdown becomes too much of a pain.

### GitHub Pages
I'm using GitHub Pages to host this site, simply because it's free to set up and code changes are instantly deployed. I then added my custom domain to the GitHub Pages settings, and set up a CNAME record in my domain hoster DNS to direct it here.

## Creating a Hugo website

First, install Hugo and Git on your machine. I'm on Windows and used the [Chocolatey](https://chocolatey.org/) package manager to install Hugo. On Linux/MacOS you might want to use Homebrew.

Run these commands to create a basic site
```
hugo new site quickstart
cd quickstart
git init
git clone https://github.com/gurusabarish/hugo-profile.git
 themes/hugo-profile
echo "theme = 'hugo-profile'" >> config.toml
hugo server
```

Add your first page on the site.
```
hugo new blogs/hello-world.md
```

Hugo created the file in the content/posts directory. Open the file with your editor.

```
---
title: "Hello World"
date: 2023-01-05T11:19:35Z
draft: true
---
```

Note the `draft` value. Hugo won't publish the post while this is set to "true".

Add some content below the header, in the body of the post:

```
---
title: "Hello World"
date: 2023-01-05T11:19:35Z
draft: true
---
## My first blog

Hello world! 

This is **bold** text, and this is *emphasized* text.

Visit the [Hugo](https://gohugo.io) website!
```

Save the file, then run the follow command to run Hugo’s development server to view the site. The `-D` flag tells the server to include draft content.

```
hugo server -D
```

With your editor, open the site configuration file (config.toml) in the root of your project.

```
baseURL = 'http://example.org/'
languageCode = 'en-us'
title = 'My Portfolio Site'
theme = 'ananke'
Make the following changes:
```

Set the baseURL for your production site. This value must begin with the protocol and end with a slash, as shown above.

Set the languageCode to your language and region.

Set the title for your production site.

Start Hugo’s development server to see your changes, remembering to include draft content.

hugo server -D