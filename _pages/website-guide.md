---
permalink: /guide/
title: "How to Use Our Family Blog"
---

Dear Christina,

**Happy Birthday!** I want us to have this nice website for our family so we can share pictures of our adventures and also of our basic day to day stuff.

Please refer to this guide to learn how to write pages for our joint website! It'll help you setup your computer with a Github directory (I know, I know - but trust me it's worth it!) and write blog posts like a pro.

Obviously, I'm always here to help and I want to keep this guide nice and current and helpful so let me know if you need anything!

I want this website to be a way to share our adventures and photos with everyone. I know it's the kind of gift that's really just a bunch of work, but I think it's worth it! After you get used to the workflow I lay out below, it'll be easy to write new posts after we take trips, have big events, or just capture little memories that we want to share. This method is basically free (just ~$10 a year for owning *www.mccoybowman.com*), future-proof, flexible, and (I think) kind of fun!


# Table of Contents

1.  [Setting up the computer](#orgdac4776)
    1.  [Install Git](#org68db785)
        1.  [Optional: Install Jekyll for local website editing](#orgad3cd25)
    2.  [Configure your local directory](#org77a7b35)
2.  [Blogging](#org5287fe0)
    1.  [How to create a post](#org7b26b67)
    2.  [Writing our blog!](#orgd68688a)
        1.  [Adding images](#orge77ab33)
    3.  [Pushing our website to Github Pages.](#orgc50ea0f)
    4.  [The Github Workflow.](#org04a8664)
3.  [Wrapping Up](#org37804a1)

<a id="orgdac4776"></a>

# Setting up the computer

I'm happy to do this part for you, but it's kind of fun to learn about the nuts and bolts of everything. If you just want a working version of the website on the computer, then just ask me to do it and I'll set it up. If so, skip down to [Blogging](#org5287fe0).


<a id="org68db785"></a>

## Install Git

The first step to being able to edit the website on your computer is to install git. If you're using your Pixelbook (which you probably are) then fire up your terminal and type:

`sudo apt install git`

and let the computer do its thing. Done!


<a id="orgad3cd25"></a>

### Optional: Install Jekyll for local website editing

Having Jekyll installed locally is nice because you can run your website on you computer (i.e. not on the Internet at Github pages) to see how things look. Otherwise you have to push your website changes to Github and wait for your domain to update.

I haven't included those instructions here yet, but I can if you would like me to.


<a id="org77a7b35"></a>

## Configure your local directory

I like to have my blog live in a folder in my home directory called `blogs`. This directory houses my personal website and our joint website. So do:

`mkdir blogs && cd blogs`

Now we clone our site into this directory from Github. Run:

`git clone https://github.com/alexchristina/alexchristina.github.io.git`

Which creates a new directory, `alexchristina.github.io` in `~/blogs`.

*By the way! In Linux,* `~` *is a shortcut for* `/home/username/` *so the syntax* `~/blogs/` *is the same thing as* `/home/username/blogs`.

Now, `cd` into this directory:

`cd alexchristina.github.io`

and view its contents with `ls`:

`ls`

which should give you a readout like:

`assets       _data         index_default.html  _pages     _site`
`CNAME        Gemfile       index.html          _posts         ~
~_config.yml  Gemfile.lock  index-splash.html   README.md`

This is your website! It doesn't look like it yet, but it is!


<a id="org5287fe0"></a>

# Blogging


<a id="org7b26b67"></a>

## How to create a post

Posts are for blog-style updates with dates. They are stored in the `_posts` directory of our website folder with the format:

`` `yyyy-mm-dd-post-title.md ``

So let's first navigate to our directory with:

`cd ~/blogs/alexandchristina.github.io/_posts`

Now that we're in the right directory,  let's make a new post with our text editor and call it `2019-09-22-mommys-birthday.md`.

*Optional: It might be easier to use a draft template. Drafts are* `.md` *files with no date. They live in the* `_drafts` *folder. For example, we can use the* `standard.md` *template by executing the following command from our blog's root directory:*

`cp _drafts/standard.md _posts/2019-09-22-mommys-birthday.md`

*Which copies a good starting template to a new file with our desired file name.*

Now let's edit our file. At the top is the **Front Matter** which tells Jekyll some important info. It's pretty intuitive to edit this stuff. Make sure the title is correct and, since we're writing a blog post about Christina, add a Christina tag!

Now we're ready to edit the main body of the website!


<a id="orgd68688a"></a>

## Writing our blog!

Everything under the `---` in the front matter is fair game for editing our blog. So, just type some text! Let's write:

> Mommy was so happy to celebrate a birthday with her son for the very first time.

This text will be automatically rendered on our webpage, which is cool.


<a id="orge77ab33"></a>

### Adding images

I wish I could say that images are just "drag and drop" but unfortunately they're a bit fussy. Once you get used to it, it's not so bad. The short answer is that all images for our website live in the `/assets/images` folder in the root of our blog, so:

`/home/alzxjm/blogs/alexchristina.github.io/assets/images`

You don't have to type that every time: you can just start with the `/assets` part and go forward from there. So, to add a photo, we use the Markdown syntax:

`![Image Title](/path/to/image.jpg)`. If we want to insert an image into our page, we write:

`![Mommy and Q](/assets/images/christina-and-q.jpg)`

Now, obviously we need to put a photo in that location, too. My workflow goes something like this:

1.  Go to Google Photos and pick a photo I want to put on the website.
2.  Do all the edits I want to this photo, then download it.
3.  Photos taken on our phones have a kind of nonsense syntax that's not important to our blog, so I save the photo with a human-readable title, like `christina-and-q.jpg`.
4.  Make sure to save this photo in `/assets/images/`.

Now, our website will display the photo on our blog post! 


<a id="orgc50ea0f"></a>

## Pushing our website to Github Pages.

So we've modified all our website pages and photos locally and we want to see how they look on the Internet version of the website. This involves a few git steps:

1.  Make sure you're in your website's home directory, i.e `/blogs/alexchristina.github.io`.
2.  Run the command `git add .`. This scans the git directory for any new files and marks them to be uploaded.
3.  Now run `git commit -m "Mommy birthday blog post"` which tells Github to commit the changes you've made and stage them to be pushed.
4.  Finally, execute: `git push origin master` which actually does the pushing. It will ask you for your Github credentials at this point, which I will make sure to give you.

And that's it! The website should now be available to view at <https://www.mccoybowman.com>.


<a id="org04a8664"></a>

## The Github Workflow.

When you want to work on your website, you should do the following:

1.  Navigate to your blog's directory.
2.  Run `git pull` which updates your local copy of the website with the current one on Github.
3.  Make your changes (create new posts, download photos, etc.)
4.  Run those conmmands from above to update the new website. Make sure to add a comment to the `git commit -m` line that helps you track the changes you've made over time!


<a id="org37804a1"></a>

# Wrapping Up

So those are the basics! I'll be updating this page over time to add more advanced things, like changing page layouts, updating the About section, etc.etc. I hope you've found this useful!

Love,
Alex

