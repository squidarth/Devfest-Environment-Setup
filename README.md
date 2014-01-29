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

### Opening up Terminal (Mac only)

Terminal is going to be where most of our development-related software will
be running.  Simply use Spotlight to open it up

![terminal open](https://raw2.github.com/squidarth/environment-setup/master/static/open_terminal.png)

### Installing Git

Git is necessary on both Mac and PC to get environments set up.  First, check
if it has been installed already by loading up Terminal and typing
`git`, followed by hitting ENTER.
If git is installed, you should see the following output:

![git output](https://raw2.github.com/squidarth/environment-setup/master/static/git_output_success-3.png)

If not, install git from the [git website](http://git-scm.com/downloads), where
there are more instructions.

### Installing VirtualBox

To make development simpler, we will be doing our development in a Virtual Machine.
The simplest way to do this is by using a piece of software called [vagrant](http://vagrantup.com).
The first dependency for Vagrant is VirtualBox. To install this, visit [the VirtualBox website](https://www.virtualbox.org/wiki/Downloads)
and download the version for your operating system.

![virtualbox page](https://raw2.github.com/squidarth/environment-setup/master/static/virtualbox_downloads-2.png).

Simply go through the installer until it's finished.

![virtualbox installer](https://raw2.github.com/squidarth/environment-setup/master/static/virtualbox_installer-2.png)

### Installing Vagrant

Next, we need to install Vagrant, which is an easy way to manage VirtualBox
Virutal Machines.  To do this, visit the [Vagrant website](http://www.vagrantup.com/downloads.html)
and install the appropriate version for your Operating System.

![vagrant website](https://raw2.github.com/squidarth/environment-setup/master/static/vagrant_downloads-2.png)

Once it has been installed, load up your terminal again and type `vagrant`.

You should see the following output:

![vagrant output](https://raw2.github.com/squidarth/environment-setup/master/static/vagrant_output-2.png)

If you see this, then you're ready to start developing!

### Basic Terminal Use

The next couple steps will require knowing a few terminal commands.  The terminal
is often called the "Command Line", and we'll be using that terminology for the
rest of this short guide.  In order to execute commands in the command line (which
you have already done a couple times), type the command and then hit "enter".

When you are using the command line, you are always in a certain directory.  To
check the directory you are in, simply run `pwd`.

![pwd usage](https://raw2.github.com/squidarth/environment-setup/master/static/pwd_usage-2.png)

To list all the files in the current directory you are in, type the command `ls` (list).

![ls usage](https://raw2.github.com/squidarth/environment-setup/master/static/ls_usage-2.png)

To change directories, type the `cd` command, followed by the name of the directory
that you would like to navigate to.  Note that `~` is the name of your home
directory (the directory where your Documents directory is).

![cd usage](https://raw2.github.com/squidarth/environment-setup/master/static/cd_usage-2.png)


### Getting started with Vagrant

Now you should be ready to get started using Vagrant to do some web development.

First, navigate to a directory where you would like to start writing code.

![move to devfest](https://raw2.github.com/squidarth/environment-setup/master/static/move_to_devfest-2.png)

Then, type the command  `git clone https://github.com/adicu/flask_test.git`

![git clone usage](https://raw2.github.com/squidarth/environment-setup/master/static/git_clone_usage-2.png)

What this does is create a directory in the current folder you are in called
"flask_test", and uses Git, which we installed earlier, to load into that project
a sample project that we have prepared for you.

Now, we'll be passing around a thumb drive with some files on it at this point,
if you had the opportunity to grab files off the thumb drive instead of having
  to download them, here's what you'll need to do to use it with Vagrant:

Open up the file in the `flask_test` directory called `Vagrantfile` in any
text editor.  It will look like this:

![vagrantfile original](https://raw2.github.com/squidarth/environment-setup/master/static/original_vagrantfile-2.png)

Move a file called `precise32.box` from the thumb drive to any directory on your 
computer, and then change the line that reads `config.vm.box_url = "http://files.vagrantup.com/precise32.box"`
to point to the precise32.box file you got from your computer.  For example,
if you put it in a folder called `~/Downloads`, then, this line should read
  `config.vm.box_url = "~/Downloads/precise32.box"`.  If you didn't get a chance
  to get files from the thumb drive, don't worry about this step and move on.

To start the virtual machine for this project, first move to the "flask_test"
directory, and run the command `vagrant up`.

![vagrant up](https://raw2.github.com/squidarth/environment-setup/master/static/vagrant_up-2.png)

Once this command finishes executing (it will take a couple minutes), your
virtual machine will be ready to use.  To access the machine, use the command

`vagrant ssh`.  Once this command has finished executing, you will be inside
a virtual machine different from your own machine. To return to your local machine,
simply type the command `exit`.

The special thing about Vagrant is that you have access inside the Virtual
Machine to files on your local computer.  Once inside the Virtual Machine,
type

`cd /vagrant`, followed by `ls`, and you'll see that the files in the "flask_test"
folder on your computer are available on this virtual machine.  To prove to yourself
that everything is working, type `python src/application.py`, and open up your
browser to [http://localhost:5000](http://localhost:5000/).

This is all demonstrated here:

![vagrant ssh](https://raw2.github.com/squidarth/environment-setup/master/static/vagrant_ssh-2.png)

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

Second, there are a couple important files in the `flask_test` folder that you
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
