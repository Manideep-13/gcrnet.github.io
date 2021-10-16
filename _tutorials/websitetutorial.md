---
layout: post
title: Jekyll static site generator
feature-img: "assets/img/pexels/computer.jpeg"
date: 14 August 2020
---
Jekyll is really useful for building static websites. You can use a Jekyll theme to write posts using markdown with less amount of HTML, CSS, and have a responsive good looking website. If you are a developer who loves to create websites while having control of every single aspect of HTML and CSS, Jekyll allows for all of that. You can create your own themes, layouts, control, and configure the entire site.

We will present enough information to get you started with your first Jekyll website, from creating content to serving them on Github pages.

1. [Research](#research)
2. [Installation](#install)
3. [Creating a site](#create)
4. [Front matter](#front)
5. [Config.yaml](#config)
6. [Installing themes](#themes)
7. [Layouts](#layouts)
8. [Includes](#includes)
9. [Hosting on Github pages](#hosting)
10. [Wiki](#wikki)


<a name="research"></a>
## Research


<a name="install"></a>
## Installation
The Jekyll website provides [installation](https://jekyllrb.com/docs/installation/) instructions that cover Windows, Mac, and Linux operating systems.

<a name="create"></a>
## Creating a site
For this tutorial, we will name our website "test_blog". Issue the command below at the terminal to create your new site.
```yml
jekyll new test_blog
```

<img src="/assets/img/tutorialsimages/jekyll/1.png" >

Jekyll creates some default content for the new site.

<img src="/assets/img/tutorialsimages/jekyll/2.png" >
Change directory into the `test_blog` directory
```yml
cd test_blog
```
Run the command below at the terminal and Jekyll will take all the pieces of our website and serve them in our browser. Browse the displayed server address `http://127.0.0.1:400/` to see the content of the website. You can also stop the display with the command `ctrl-c`
```yml
bundle exec jekyll serve
```
<img src="/assets/img/tutorialsimages/jekyll/3.png" >

The local host server now displays the new website from the browser.

<img src="/assets/img/tutorialsimages/jekyll/4.png" >
                                       
`test_blog`: the root directory                      
`_posts`: folder with all the blog posts.  
`_site`:  folder with the final output of the website.  
`_config.yaml`: file with the settings and basic attributes of the site.    
`Gemfile`: holds all the dependencies for the website.    
The rest of the files just default basic parts of our website.

<a name="front"></a>
## Front matter
[Front matter](https://jekyllrb.com/docs/front-matter/) is the site attribute
such as `Title` and `author's name` and many others, depending on our preference.
Jekyll reads the front matter first when a file is being executed to check the
layout specifications. See the example below.

```
---
layout: post
title: Jekyll static site generator
date: 14 August 2020
author: Joe Doe
---
```

We see some special information at the top of our post which is different from the content, That is called front matter.

<a name="config"></a>
## Config.yaml
config.yaml file has the settings and basic attributes of the site.

```yml
title: Your awesome title
author:
  name: GitHub User
  email: your-email@domain.com
description: > # this means to ignore newlines until "show_excerpts:"
  Write an awesome description for your new site here. You can edit this
  line in _config.yml. It will appear in your document head meta (for
  Google search results) and in your feed.xml site description.
show_excerpts: false # set to true to show excerpts on the homepage

# Minima date format
# refer to https://shopify.github.io/liquid/filters/date/ if you want to customize this
minima:
  date_format: "%b %-d, %Y"

  # generate social links in the footer
  social_links:
    twitter: jekyllrb
    github:  jekyll
    # devto: jekyll
    # dribbble: jekyll
    # facebook: jekyll
    # flickr:   jekyll
    # instagram: jekyll
    # linkedin: jekyll
    # pinterest: jekyll
    # youtube: jekyll
    # youtube_channel: UC8CXR0-3I70i1tfPg1PAE1g
    # youtube_channel_name: CloudCannon
    # telegram: jekyll
    # googleplus: +jekyll
    # microdotblog: jekyll
    # keybase: jekyll

    # Mastodon instances
    # mastodon:
    # - username: jekyll
    #   instance: example.com
    # - username: jekyll2
    #   instance: example.com

    # GitLab instances
    # gitlab:
    # - username: jekyll
    #   instance: example.com
    # - username: jekyll2
    #   instance: example.com

# If you want to link only specific pages in your header, uncomment
# this and add the path to the pages in order as they should show up
#header_pages:
# - about.md

# Build settings
theme: minima

plugins:
 - jekyll-feed
 - jekyll-seo-tag
```
Above is an example config.yaml file of `jekyll-minimal` theme. As said earlier this has all the basic configurations and settings of the website.


<a name="themes"></a>
## Installing themes
By default, we will be having a minima theme for our Jekyll website. If we want a different theme for our website, there are lots of freely available themes on the internet.

Website for free themes:
 * [Jekyll themes](http://jekyllthemes.org/)
 * [Free jekyll themes](https://jekyll-themes.com/free/)

You can find many other good websites on the internet.

We will be showing an example of the theme change.
Every theme has a link to the Github repository which shows exactly how to use the theme in the `readme.md` section.
For the example, we selected a "Jekyll-hacker theme" from the internet. We will read the instructions on how to use it and install it. We will show the difference between the Jekyll minima theme and the new theme.

<img src="/assets/img/tutorialsimages/jekyll/5.png" >

We can see the theme change.

So basic steps to follow once you select a theme are,
 In the gem file add your selected theme, then install the theme by the command below.
```yml
bundle install
```
Change the theme attribute in the `_config.yaml` file and restart the server with the command below.
```yml
bundle exec jekyll serve
```
 
 <mark> Do not forget to change the layout names in your posts according to the theme you selected. If you don't change the layout you will not see the changes once you restart the server. </mark>

<a name="layouts"></a>
## Layouts
Layouts are skeletons of HTML code used to define the looks and feels of different pages or your entire site. By default, Jekyll will provide layouts for our pages. If you want to create your own layout.
1. Go to the root directory and create the `_layouts` folder.
2. Create an html file of your own and start making your own layout.

In the `_layouts` folder creating your own layout looks like this.
The code snippet below is an example of a layout called "`Home.html`" which uses the default layout.
```
---
layout: default
---

<div class="home">

    <div id="main" class="call-out"
         style="background-image: url('{{ site.header_feature_image | relative_url }}')">
        <h1> {{ site.header_text | default: "Change <code>header_text</code> in <code>_config.yml</code>"}} </h1>
    </div>
</div>

```

After you create your own layout, you can switch your site layout to it, which will then show up.

<a name="includes"></a>
## Includes
Includes allow us to take certain components of our site such as the header, the footer, or a navigation list and abstract them into their own html files. That means we can have an html file that describes the header or footer for the entire site. We can have a navigation list designed and include that on any page we want on the site. Follow the steps below to create your own layout.
1. Go to the root directory and create the `includes` folder.
2. Create a html file of your own and start to make components of your website.

In the `_includes` folder creating your own layout looks like this.
The code snippet below is an example of an include html file which creates a navigation list and can be further used anywhere on the site.

```
<div class="navigation-list">
   
<li>
<p><a href="{{ item.url | relative_url }}">{{ item.title }}</a></p>
</li>
   
</div>

```

The include file can be included in any part of your website.

<a name="hosting"></a>
## Hosting on Github pages
Github pages (gh-pages) is a service that Github offers and allows you to build and host a static website completely for free. Jekyll integrates with gh-pages very well.

Setting up and hosting a static site in gh-pages:
1. Create a Github account.
2. Install git on your computer.
3. Create a new repository and name that, `test_blog`. Do not initialize a readme file.
<img src="/assets/img/tutorialsimages/jekyll/6.png" >
4. After creating the repository, we need to edit a variable in the config.yaml file.
   * Edit `baseurl` attribute.
   * Add the website name into the base URL, in this case, it is `test_blog`.
   * If you are planning on using a custom domain name you need to put that in the base URL.
<img src="/assets/img/tutorialsimages/jekyll/7.png" >
5. Set up a Github repository inside of the Jekyll project and upload it into Github.

Git commands for creating a repository and uploading all files to Github :
1. `git init` <br>
This will initialize an empty repository.
2. `git chechout -b gh-pages` <br>
We need to store our files on the gh-pages branch of our repository. The above command will checkout the gh-pages branch.
3. `git add .` <br>
This will add all our files to staging.
4. `git commit -m "initial commit"`<br>
This is an initial commit.
5. `git remote add origin "add your repository address here"`<br>
6. `git push origin gh-pages` <br>
This will upload all the files to the gh-pages.

<img src="/assets/img/tutorialsimages/jekyll/8.png" >

After you upload you will see all the files in Github

<img src="/assets/img/tutorialsimages/jekyll/9.png" >

You can go to the settings tab and scroll down you will see "your site is published."

<img src="/assets/img/tutorialsimages/jekyll/10.png" >

You can use that link to visit your static website.

<a name="wiki"></a>
## Wiki

[Here](https://www.youtube.com/watch?v=T1itpPvFWHI&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB) is a link to a video tutorial by Giraffe academy.
This tutorial is very helpful for more detailed information.

