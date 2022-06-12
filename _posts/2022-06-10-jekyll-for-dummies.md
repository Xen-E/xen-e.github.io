---
title: Jekyll simplified
description: What is Jekyll and other static site generators? Learn here.
category: How-To
tags:
- Jekyll
- Web
- Static
- Install
- Github
---

## What is Jekyll?
Jekyll is a **static** web pages generator. A normal regular websites usually work **dynamically**, That means they communicate in real-time with databases or Interpreters...etc. For example; A dynamic website will use languages such as *PHP*, *Python*, *Perl*, *Ruby*...and other script languages, All these require a interpreter in order to execute and talk back to the website which is most likely is hosted on the same server. It's a long process that takes a lot of resources and time. from both; The server and the client (you).<!--more-->

A static website is a set of web pages that use pure *HTML*, *CSS* and maybe sometimes *Javascript* if necessary. You may wonder how these type of websites function at all? or how they serve certain data to the user? The answer is Jekyll! OR other static website generators, They have their own basic script languages which you're going to use in your HTML files, they called **Templates**. after that you run the generator and let it do work!

As for data it can be stored in a local file and accessed directly though IO. JSON files for example make an excellent option instead of MySQL, PostgreSQL or other heavy dynamic database management systems.

Static websites are blazing fast and very light on the server because they're just pure HTML/CSS files which they get rendered by the web browser engine very easily and in microseconds or milliseconds. Plus these files are very small in size, you can have a full website riddled with data and it will be less than 1MB!

## Origins
Jekyll is a **Ruby Gem**, that means it was written in Ruby programming language and released as a package you can install from the command-line, **RubyGems** is a package manager; Something like cargo for rust or npm for nodejs.

Jekyll uses a markup language called [Liquid](https://github.com/Shopify/liquid). It's a simple, safe, easy to learn language that can be used to write templates. It has most functionalities you need! Like:

* Variables
* Iteration/Loops (for, break, continue)
* Conditional Statements (if, elsif, else, unless)
* Switch Statement (case, when)
* Much more!

The other markup language Jekyll also uses is the famous **Markdown** format, Which is lot simpler and mostly used when writing posts/pages or any file with the **.md** or **.markdown** extension.

The author of Jekyll is the co-founder of Github: **Tom Preston-Werner**. He worked on this project back in 2008 and then a lot of other developers started to contribute.

## Installation
One of the best way to experience Jekyll is to use [Github pages](https://pages.github.com), A 100% free service for you as a open source contributor; But also can be independently installed and configured on any server of your choice.

As i mentioned before, Jekyll is a ruby gem and can be installed through the command-line. That means you need to have a toolchain ready like the Ruby programming language and the RubyGems package manager and maybe the GCC compiler as well, but the first two are required.

If you're on Windows and things looking difficult then read the following tutorial i did on how to create a toolchain in Windows: [How to easily setup a Toolchain in Windows (Any Language)](https://xen-e.github.io/dev/2022/06/09/windows-toolchain.html).

First of all make sure you have the GCC installed on your machine just in case:
```bash
pacman -S --needed base-devel mingw-w64-x86_64-toolchain
```
And then:
```bash
pacman -S mingw-w64-x86_64-ruby
```
For 32bit version (Ruby):
```bash
pacman -S mingw-w64-i686-ruby
```
Now verify everything is functioning by typing:
```bash
gcc --version
make --version
ruby -v
gem -v
```
If they're installed and ready then now you can start installing Jekyll by using:
```bash
gem install jekyll bundler
```
That's it! For full detailed installation guide on how to get Jekyll on different systems then check out [this guide](https://jekyllrb.com/docs/installation).

## Usage
The first thing we should do now is to start a new static website, So pick a directory/folder and open the terminal/command-line in it and then:
```bash
jekyll new blog
```
Enter the directory:
```bash
cd blog
```
Now let's create a local host with the new static website:
```bash
bundle exec jekyll serve
```
*Note: If you are using Ruby version 3.0.0 or higher, step 5 may fail. You may fix it by adding **webrick** to your dependencies: **bundle add webrick***

Head over to [localhost:4000](http://localhost:4000)!

Remember to read the new website files because they contain important comments explaining how they work and how they can be modified.

Here's the directory structure of a average Jekyll website:

| File/Directory | Description |
| -------------- | ----------- |
| **_config.yml** | Stores configuration data. Many of these options can be specified from the command line executable but it’s easier to specify them here so you don’t have to remember them. |
| **_drafts** | Drafts are unpublished posts. The format of these files is without a date: **title.MARKUP**.
| **_includes** | These are the partials that can be mixed and matched by your layouts and posts to facilitate reuse. The liquid tag **{% raw %}{% include file.ext %}{% endraw %}** can be used to include the partial in *_includes/file.ext*.
| **_layouts** | These are the templates that wrap posts. Layouts are chosen on a post-by-post basis in the front matter, which is described in the next section. The liquid tag **{%raw%}{{ content }}{%endraw%}** is used to inject content into the web page.
| **_posts** | Your dynamic content, so to speak. The naming convention of these files is important, and must follow the format: **YEAR-MONTH-DAY-title.MARKUP**. The permalinks can be customized for each post, but the date and markup language are determined solely by the file name.
| **_data** | Well-formatted site data should be placed here. The Jekyll engine will auto-load all data files (using either the *.yml, .yaml, .json, .csv* or *.tsv* formats and extensions) in this directory, and they will be accessible via **site.data**. If there's a file **members.yml** under the directory, then you can access contents of the file through **site.data.members**.
| **_sass** | These are sass partials that can be imported into your **main.scss** which will then be processed into a single stylesheet **main.css** that defines the styles to be used by your site.
| **_site** | This is where the generated site will be placed (by default) once Jekyll is done transforming it. It’s probably a good idea to add this to your *.gitignore* file.
| **.jekyll-cache** | Keeps a copy of the generated pages and markup (e.g.: markdown) for faster serving. Created when using e.g.: *jekyll serve*. Can be disabled with an option and/or flag. This directory will not be included in the generated site. It’s probably a good idea to add this to your *.gitignore* file.
| **.jekyll-metadata** | This helps Jekyll keep track of which files have not been modified since the site was last built, and which files will need to be regenerated on the next build. Only created when using incremental regeneration (e.g.: with *jekyll serve -I*). This file will not be included in the generated site. It’s probably a good idea to add this to your *.gitignore* file.
| **index.html/index.md/other HTML, Markdown files** | Provided that the file has a front matter section, it will be transformed by Jekyll. The same will happen for any *.html*, *.markdown*, *.md*, or *.textile* file in your site’s root directory or directories not listed above.

Keep in mind that every file or directory beginning with the following characters: **.**, **_** , **#** or **~** in the source directory will not be included in the destination folder. Such paths will have to be explicitly specified via the config file (**_config.yml**) in the include directive to make sure they’re copied over:

```bash
include:
 - _pages
 - .htaccess
```

If you want To publish your new static Jekyll website after you finished modifying it you can either:
1. Use the regular **git push** after done committing (*git add .* / *git commit -m "Hi!"* / *git push origin master*). Push this repository to your Github account/repo. [More](https://pages.github.com).
2. Use the "*jekyll build*" command to build your static website which is going to be generated in the **_site** directory. Then simply upload that directory (**_site**) to your web server though FTP into your root folder, This is most likely to be the **httpdocs** or **public_html** folder on most hosting providers.

That's it! If you want an example of a Jekyll website then just continue browsing this site because i use it myself!

Bonus: [Add pagination to your Github page or Jekyll website](https://xen-e.github.io/how-to/2022/05/22/jekyll-pagination.html)