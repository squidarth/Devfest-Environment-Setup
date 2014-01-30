# Devfest Environment Setup

### Motivation

During Devfest this year, we will be using a piece of software called
Vagrant for our development.  Vagrant allows users to really easily manage
Virtual Machines, which are basically operating systems running on top of your
current operating system, which we can use for our own software development.

Writing code on a virtual machine has a number of advantages over doing so
locally on your computer.  Most importantly, installing software for development
is often one of the most frustrating things about getting started.  We have
provisioned a virtual machine with all the software you need--so that regardless
of whether you run a PC or a Mac, you can be up and running as soon as you have
Vagrant installed.


### A Note on Writing Code

All programmers have a text editor that they use to write code.  If you're just
getting started, we highly recommend you download and install [Sublime Text](http://www.sublimetext.com/2).

### Opening up Terminal (Mac only)

Terminal is going to be where most of our development-related software will
be running.  Simply use Spotlight to open it up

![terminal open](http://squidarth.github.io/static/open_terminal.png)

## Open up Command Prompt (PC onlY)

The PC equivalent of Terminal is a program called "Command Prompt".  To open it,
click the "Start Menu", navigate to "Accessories", and click "Command Prompt"

### Installing Git

Git is necessary on both Mac and PC to get environments set up.  First, check
if it has been installed already by loading up Terminal and typing
`git`, followed by hitting ENTER.
If git is installed, you should see the following output:

![git output](http://squidarth.github.io/static/git_output_success-3.png)

If not, install git from the [git website](http://git-scm.com/downloads), where
there are more instructions.

### PC Instructions

On PCs there are a couple extra steps in installing git that you should be
aware of.

Start out by going through the git installation normally, using the installer
that you downloaded from the [git website](http://git-scm.com/downloads).

![git install](http://squidarth.github.io/static/git_install_msft.PNG)

Once you reach this screen:

![git install](http://squidarth.github.io/static/git_setup_msft.PNG)

Select the option that reads "Run Git and included tools from the Windows Command Prompt".
This is very important!

To make sure that git was installed correctly, open up the Windows Command Prompt
and type `git`.  You should see the following output:

![git install](http://squidarth.github.io/static/git_successful_msft.PNG)

### Installing VirtualBox

To make development simpler, we will be doing our development in a Virtual Machine.
The simplest way to do this is by using a piece of software called [vagrant](http://vagrantup.com).
The first dependency for Vagrant is VirtualBox. To install this, visit [the VirtualBox website](https://www.virtualbox.org/wiki/Downloads)
and download the version for your operating system.

![virtualbox page](http://squidarth.github.io/static/virtualbox_downloads-2.png).

Simply go through the installer until it's finished.

![virtualbox installer](http://squidarth.github.io/static/virtualbox_installer-2.png)

### Installing Vagrant

Next, we need to install Vagrant, which is an easy way to manage VirtualBox
Virutal Machines.  To do this, visit the [Vagrant website](http://www.vagrantup.com/downloads.html)
and install the appropriate version for your Operating System.

![vagrant website](http://squidarth.github.io/static/vagrant_downloads-2.png)

Once it has been installed, load up your terminal again and type `vagrant`.

You should see the following output:

![vagrant output](http://squidarth.github.io/static/vagrant_output-2.png)

If you see this, then you're ready to start developing!

### Basic Terminal Use


The next couple steps will require knowing a few terminal commands.  The terminal
is often called the "Command Line", and we'll be using that terminology for the
rest of this short guide.  In order to execute commands in the command line (which
you have already done a couple times), type the command and then hit "enter".

#### Mac

When you are using the command line, you are always in a certain directory.  To
check the directory you are in, simply run `pwd`.

![pwd usage](http://squidarth.github.io/static/pwd_usage-2.png)

To list all the files in the current directory you are in, type the command `ls` (list).

![ls usage](http://squidarth.github.io/static/ls_usage-2.png)

To change directories, type the `cd` command, followed by the name of the directory
that you would like to navigate to.  Note that `~` is the name of your home
directory (the directory where your Documents directory is).

![cd usage](http://squidarth.github.io/static/cd_usage-2.png)

#### PC

On PCs, similarly to Mac, in the command prompt, you are always in a certain directory,
and the path is listed in your prompt, so you always know what directory you
are in.

`cd` is used to change directories, very similarly to how this is done on Macs.
Note that on PCs, `\` is used in writing out directory paths, rather than the
`/` used on Macs.

`dir` is used to list files and directories inside folders.

### Getting started with Vagrant

Now you should be ready to get started using Vagrant to do some web development.

At this top of the page, you should be able to download a zip file that contains
three files, `Vagrantfile`, `bootstrap.sh`, and `README.md`.  Copy `Vagrantfile`
and `bootstrap.sh` to a directory in which you would like to start writing
code.

![move to devfest](http://squidarth.github.io/static/move_to_devfest-2.png)


Now, we'll be passing around a thumb drive with some files on it at this point,
if you had the opportunity to grab files off the thumb drive instead of having
  to download them, here's what you'll need to do to use it with Vagrant:

Open up the file called `Vagrantfile` in any
text editor.  It will look like this:

![vagrantfile original](http://squidarth.github.io/static/original_vagrantfile-2.png)

Move a file called `precise32.box` from the thumb drive to any directory on your 
computer, and then change the line that reads `config.vm.box_url = "http://files.vagrantup.com/precise32.box"`
to point to the precise32.box file you got from your computer.  For example,
if you put it in a folder called `~/Downloads`, then, this line should read
  `config.vm.box_url = "~/Downloads/precise32.box"`.  If you didn't get a chance
  to get files from the thumb drive, don't worry about this step and move on.

To start the virtual machine for this project, first move to your project 
directory, and run the command `vagrant up`.

![vagrant up](http://squidarth.github.io/static/vagrant_up-2.png)

Once this command finishes executing (it will take a couple minutes), your
virtual machine will be ready to use.  To access the machine, use the command

`vagrant ssh`.  Once this command has finished executing, you will be inside
a virtual machine different from your own machine. To return to your local machine,
simply type the command `exit`.

The special thing about Vagrant is that you have access inside the Virtual
Machine to files on your local computer.  Once inside the Virtual Machine,
type

`cd /vagrant`, followed by `ls` (`dir`) on PC, and you'll see that the files in your
folder on your computer are available on this virtual machine.

(PC Only) Here is what you should see if you're on a PC:

![vagrant success](http://squidarth.github.io/static/vagrant_success_msft.png)

A couple other important commands to note are `vagrant halt` and `vagrant reload`.
`vagrant halt` stops the Virtual Machine, while `vagrant halt` restarts it.  These
commands should be your first line of defense if anything seems to be going wrong.

### Remarks on Vagrant Usage (Optional)

Congratulations, you now have Vagrant set up successfully!  In this section,
I'd just like to note a couple things about using Vagrant.

First of all, even though when you are connected to your Vagrant box (what happens after
typing `vagrant ssh`), you are on a Virtual Machine, the files in the `/vagrant`
folder are actually the same files on your Mac or PC.  This means that you can
edit those files in any text editor you like, and the changes will immediately
be reflected in Vagrant.

Second, there are a couple important files that you
should be aware of.  First is the file called `Vagrantfile`.  This file specifies
the configuration of Vagrant box.  If you would like to use Vagrant in a different
project, you can copy this file over to that directory, and then type `vagrant up`
in that directory to get started using Vagrant with that new project.

The other file to be aware of is the file called `boostrap.sh`.  This file is
a script that provisions the Vagrant box with software needed to start developing
web applications in Python using the Flask framework.  If you are starting another
similar project, copy this file to your new project folder as well.

### Common Gotchas

Unfortunately, some people do run into some minor problems with Vagrant.  By
far the most common problem is the command `vagrant up` or `vagrant halt` hanging and running forever.
This usually happens after somebody has put their computer to sleep and has
started the computer again. This can be easily remedied through the following
couple steps:

`Ctrl-C` to get the current commmand to stop.  Then, type `vagrant suspend` to
stop the box.  After this, you should be able to type `vagrant reload` to get
the box working again.

The initial `vagrant up` command might take a while because it needs to download
a ~200mb file from the web.  Subsequent `vagrant up`s will not take nearly as
long.

If nothing is working, another possibility is to destroy the VM altogether
using Virtualbox. To do this, open up VirtualBox on your machine, right-click
the box that you started, and click "Remove".

![vagrant remove](http://squidarth.github.io/static/virtualbox_remove-2.png)
