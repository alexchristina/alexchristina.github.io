
# Table of Contents

1.  [Setting up your computer and blogging setup](#orgca7c89e)
    1.  [Brief overview of the Linux command line](#org35cd132)
    2.  [Install required packages](#orgeb90b88)
        1.  [How to install programs in Linux.](#org4482d9f)
        2.  [Installing components required by Jekyll](#org02b0106)
        3.  [Installing Jekyll itself](#orga8c51e3)
    3.  [Setting up local instance of the blog](#orgf8ed47d)
        1.  [Configuring local directory](#orgb1baffe)
        2.  [Installing and configuring git](#org03bca32)
        3.  [Configuring your text editor](#editor)
			1.  [Setting up Atom](#atom)
2.  [Making web pages](#org0d2f53a)
    1.  [Overview of the blog structure](#org22460e7)
    2.  [The Github workflow](#org2e301fc)
        1.  [Making sure your local directory is up-to-date](#orgfc62aa9)
        2.  [Pushing our website to Github Pages](#org69d8526)
        3.  [Advanced: using atom's built-in Github package.](#atom-github)
    3.  [Blog posts](#orgb5c4004)
        1.  [Creating a new post](#org2d1a67c)
        2.  [Writing blog posts](#org28984e7)
    4.  [How to edit and create pages](#orgd544cd0)

The guide outlines how to use our family blog from start to finish, including setting up a new computer to manage the blog locally, edit the blog, and push the changes to Github.


<a id="orgca7c89e"></a>

# Setting up your computer and blogging setup

Here is a little cheat sheet to make it easier for you to move around the blog.


<a id="org35cd132"></a>

## Brief overview of the Linux command line

What you see in your terminal is the command line, which is where you enter commands. Some people find the command line intimidating, but really it’s just a way to type text based instructions that your computer can interpret and act on. The best way to get comfortable with it is to use it for a little while.

The text in green contains your username and the machine’s name, which is `penguin` in this case. After the colon is a blue `~` which represents your home directory (don’t worry about this now) and the `$` is your command line prompt. This is where you enter commands!

In this document, command instructions will take the form:

`$ command-goes-here`

The `$` symbol indicates that everything that follows needs to be typed in and then entered with the **enter** key. When you see a line of text like this, don’t type the “$” but instead follow with everything after, and then press enter. For example, try typing:

`$ help`

When you press enter, you should see a bunch of output containing instructions for using the command line. Don’t worry about reading this now; we will tackle some other command line basics later.

In this guide I might type something like:

`$ command #some text here`

The hashtag or "octothorpe" indicates a comment for the user, and all the text followed by that symbol is ignored by the machine. I do this sometimes to explain or make comments about commands. See what happens when you enter:

`$ help # i like kitties`

For now, here are a few helpful commands and tips:

-   `clear` keeps everything tidy by clearing the window
-   `ls` lists files and directories
-   `clear` keeps everything tidy by clearing the terminal window
-   `ls` shows you the folders and files in the current directory
-   `cd [subfolder]` allows you to move to a subfolder
-   `cd ..`  Moves you back up a directory
-   `mkdir [directory]` creates a new directory

You can find a whole bunch of useful information on [this page](https://maker.pro/linux/tutorial/basic-linux-commands-for-beginners). Take a bit of time to poke around and get used to commands. For example:

-   `$ ls                # your home directory is empty so nothing shows up here`
-   `$ cd /        # takes you to the root of your OS, denoted by /`
-   `$ ls                # shows you the contents of /`
-   `$ cd home  # moves you into /home`
-   `$ ls                # the only subdirectory here is your user directory`
-   `$ cd user  # make sure to replace user with your username!`

Note that `~` is a Linux shortcut that automatically takes you back to your home directory. This is why that first prompt you saw was `username@penguin:~$` - the default directory when you open your terminal is the home directory. It is the same as `/home/username`. You can see this by executing the following commands:

`$ cd /                                # go back to the root directory`
`$ cd home/username                # back to home directory`
`$ cd /                                # one more time`
`$ cd ~                                # again, right back to your home directory`

The blue text in your terminal shows you your current directory. For example, if you navigate to `/lib/udev`, your prompt will be: `username@penguin:/lib/udev$` and all commands entered will affect files and directories in `/lib/udev`. 


<a id="orgeb90b88"></a>

## Install required packages


<a id="org4482d9f"></a>

### How to install programs in Linux.

Relative to Windows and Mac OS X, installing packages is a little different in Linux. The easiest way is to use the built-in package manager, which is “a collection of software tools that automates the process of installing, upgrading, configuring, and removing computer programs for a computer's operating system in a consistent manner.”

The version of Linux run inside the Pixelbook is based on Debian, which has its own package manager, called `dpkg`, which lets you install programs. The easiest way to interact with `dpkg` is by using a tool called `apt`. You don’t really need to know these things right now, but I find the background useful. The syntax for `apt` is (don’t type this):

`$ sudo apt-get install /package-name-here/`

Where *package-name-here* is the program/package you would like to install. For example, if you want to install the Linux image editing program Gimp, you would type:

`$ sudo apt-get install gimp`

If you entered a package name that `dpkg` recognizes, the program will begin installing a bunch of things, and may ask you to approve some stuff by typing `Y` or `n`. You may see lots of text start to scroll by in your terminal window, which is normal.

If you make a typo, say:

`$ sudo apt-get install gimpo`

or try to install an unknown program, like:

`$ sudo apt-get install kitty-scratcher`

&#x2026;nothing bad will happen and you’ll just have to try again. By the way, `sudo` is a Linux program that allows regular users to run programs with the security privileges of a different user who has more authority. By default, `sudo` invokes the powers of the user `superuser`. For this reason, `sudo` used to stand for “superuser do,” which is just a helpful piece of Linux trivia.

![img](https://imgs.xkcd.com/comics/sandwich.png)

The `sudo` command should always be used with caution, as it enables you to make permanent changes to your operating system, so be careful!

That should be enough basic info for now, so let’s install some stuff!


<a id="org02b0106"></a>

### Installing components required by Jekyll

There are several programs/packages [required by Jekyll](https://jekyllrb.com/docs/installation/). They are:

1.  **Ruby** - programming language
2.  **RubyGems** - a package manager for Ruby that manages gems, which are self-contained programs/libraries called Gems.
3.  **GCC** and **Make** - Compiler and utility, respectively, for building and maintaining programs.

Installing these things in our Linux installation is really easy! We will do them one-by-one. First of all, we know that our installation of Linux is fresh and clean and new and has very few things installed, but sometimes it can be helpful to check for packages before attempting an installation to see if they are already installed. Let’s try that with our first target, `ruby`. Type this and hit enter:

`$ ruby -v`

You should see the output:

`-bash: ruby: command not found`

which means that **Ruby** is not installed. Let’s install it! First, let’s do a tiny bit of Linux hygiene. This is likely optional, but it makes sure that your packages and OS are fully up-to-date before beginning. Enter the following commands (linked by `&&`)

`$ sudo apt-get update && apt-get upgrade`

Now that that’s out of the way, we install **Ruby**!

`$ sudo apt-get install ruby-full`

The terminal will show you a whole bunch of text, and ask you if you want to continue. Type in a `y` and hit enter to continue. When everything completes, your default prompt will show up. Now, try that same command again:

`$ ruby -v`

And now you should see a version number, which indicates that the program is installed. Success! We can now proceed with installing **GCC** and **Make** by entering:

`$ sudo apt-get install build-essential`
`$ sudo apt-get install zlib1g-dev`

If you like, confirm the installation by using:

`$ gcc -v`
`$ make -v`

Hopefully everything went well, and we can now install **Jekyll**!


<a id="orga8c51e3"></a>

### Installing Jekyll itself

Jekyll is a **Gem**, which is a self-contained program/library written in **Ruby**. There is one small administrative task we want to do first, which is to modify a file called `.bashrc` to allow us to install Jekyll as a user other than the root user. A few things:

1.  The period in front of `.bashrc` is Linux’s way of hiding files. Remember earlier when you used the `ls` command and didn’t see anything in your home directory? Try entering the same command, but with the `-a` option added on: `$ ls -a`. You should see a bunch of files that were previously hidden. the `-a` option means “all” and shows you all files, even if hidden.
2.  `~/.bashrc` is a file that tells the current terminal the user’s preferences, which are often shortcuts and aliases that spare the user from having to type in extra stuff. You don’t need to worry too much about this, but you’re about to enter some commands which will edit your `~/.bashrc` file and it’s always good to be informed! By the way, did you notice the ~ in front of the file name? Do you remember what that stands for?

So, what we’re going to do now is add a few lines to our `.bashrc` file that tells the current terminal where to find our **Gems**. One-by-one, type in the following commands, hitting enter after each one:

```
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

That out of the way, we can install Jekyll!

`$ gem install jekyll bundler`

You’ll notice that the usage is slightly different for Jekyll than it was for installing other, system-wide applications and packages. That’s because Jekyll is a gem, and is managed by Ruby.


<a id="orgf8ed47d"></a>

## Setting up local instance of the blog

<a id="orgb1baffe"></a>

### Configuring local directory


<a id="org03bca32"></a>

### Installing and configuring git

<a id="editor"></a>

### Configuring your text editor
You need a text editor to work with your local blog. You have two main options:

1. **Nano** - a primitive but simple text editor that's not terrible for small edits. Usage is dead simple and works in your termninal. If you want to edit a text file with nano, you simply open up your terminal and run `nano file.txt`. This will open up the file in your terminal. You make your edits, and when you're done, hit **Ctrl+X** to close the file and save when prompted. 
2. **Atom** - Github's editor. I think this is what you should use. It will give you a kind of development environment for your local. Blog. Getting it setup on the Pixelbook isn't trivial, but once it's done it shouldn't be too bad. Here's how to do it.

<a id="atom"></a>

#### Setting up Atom

I adapted the instructions from [atom's website](https://blog.atom.io/2018/10/02/running-atom-on-chome-os.html). You have already completed the first few steps, so you can skip to **3. Installing Atom**. 

1. Click [this link](https://atom.io/download/deb) and save the file to your home folder in the Linux files section.
2. Using the **Files** app, navigate to the `.deb` installer and install by double-clicking.
3. Launch `atom` using your Pixelbook's launcher.

This is your text editor. It is infinitely customizable, but to get quickly started, simply close any of the initial welcome windows you see and open your blog's **Project Folder** using the **File** menu or with **Ctrl+Shift+o**.

You will now see your blog's directory tree on the left side. This is cool, as you can navigate throughout and open files as you need. So, to work with a post, expand the `_posts` folder, find the `.md` file you want, and open it!

The last nifty thing you can do is setup a live Markdown preview. When you're editing a `.md` file, simply hit **Ctrl+Shift+m** to see a live preview of your page!

<a id="org0d2f53a"></a>

# Making web pages

<a id="org22460e7"></a>

## Overview of the blog structure

(Todo)

<a id="org2e301fc"></a>

## The Github workflow


<a id="orgfc62aa9"></a>

### Making sure your local directory is up-to-date

The first thing you should always do is sync your local copy of the website with what's live on Github. To do this, navigate to the blog's directory and run:

`git pull`

Now, you can proceed to update your website, say by writing a [blog post](#orgb5c4004) or editing some [pages](#orgd544cd0).


<a id="org69d8526"></a>

### Pushing our website to Github Pages

Once you've made your changes, it's time to see how they look on the Internet version of the website. This involves a few git steps:

1.  Make sure you're in your website's home directory, i.e `/blogs/alexchristina.github.io`.
2.  Run the command `git add .`. This scans the git directory for any new files and marks them to be uploaded.
3.  Now run `git commit -m "Mommy birthday blog post"` which tells Github to commit the changes you've made and stage them to be pushed. The comment in quotes is just for us humans so we can remember what changes were made when we changes something. You can add anything you like here.
4.  Finally, execute: `git push origin master` which actually does the pushing. It will ask you for your Github credentials at this point.

And that's it! The website should now be available to view at [https://www.mccoybowman.com](https://www.mccoybowman.com)


<a id="atom-github"></a>

### Advanced: using atom's built-in Github package.
Todo

<a id="orgb5c4004"></a>

## Blog posts


<a id="org2d1a67c"></a>

### Creating a new post

Posts are for blog-style updates with dates. They are stored in the `_posts` directory of our website folder with the format:

`yyyy-mm-dd-post-title.md`

So let's first navigate to our directory with:

`cd ~/blogs/alexandchristina.github.io/_posts`

Now that we're in the right directory,  let's make a new post with our text editor and call it `2019-09-22-mommys-birthday.md`.

*Optional: It might be easier to use a draft template. Drafts are* `.md` *files with no date. They live in the* `_drafts` *folder. For example, we can use the* `standard.md` *template by executing the following command from our blog's root directory:*

`cp _drafts/standard.md _posts/2019-09-22-mommys-birthday.md`

*Which copies a good starting template to a new file with our desired file name.*

Now let's edit our file. At the top is the **Front Matter** which tells Jekyll some important info. It's pretty intuitive to edit this stuff. Make sure the title is correct and, since we're writing a blog post about Christina, add a Christina tag!

Now we're ready to edit the main body of the website!


<a id="org28984e7"></a>

### Writing blog posts

WARNING: STILL NEED TO REFORMAT THIS SECTION WITH GOOD MARKUP

Everything under the \`&#x2014;\` in the front matter is fair game for editing our blog. So, just type some text! Let's write:

> Mommy was so happy to celebrate a birthday with her son for the very first time.

This text will be automatically rendered on our webpage, which is cool.

\### Adding images

I wish I could say that images are just "drag and drop" but unfortunately they're a bit fussy. Once you get used to it, it's not so bad. The short answer is that all images for our website live in the \`/assets/images\` folder in the root of our blog, so:

\`/home/alzxjm/blogs/alexchristina.github.io/assets/images\`

You don't have to type that every time: you can just start with the \`/assets\` part and go forward from there. So, to add a photo, we use the Markdown syntax:

\`\![Image Title](/path/to/image.jpg)\`. If we want to insert an image into our page, we write:

\`\![Mommy and Q](/assets/images/christina-and-q.jpg)\`

Now, obviously we need to put a photo in that location, too. My workflow goes something like this:

1.  Go to Google Photos and pick a photo I want to put on the website.
2.  Do all the edits I want to this photo, then download it.
3.  Photos taken on our phones have a kind of nonsense syntax that's not important to our blog, so I save the photo with a human-readable title, like \`christina-and-q.jpg\`.
4.  Make sure to save this photo in \`/assets/images/\`.

Now, our website will display the photo on our blog post! 


<a id="orgd544cd0"></a>

## How to edit and create pages

