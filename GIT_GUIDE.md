# Git Guide

## What is git

Git is a version control system. Imagine the following scenario:

In the company that you work for,
the soware engineers (and that includes yourself) have
worked hard to get a minimum viable product running, and it was a huge success.
After the successful release of v1.0.0,
you now want to add more features to it and release v2.0.0 at some point.
And so you start work on v2.

After lots of hard work, v2.0.0 is now ready and so you release it.
After some time, you realise that v2.0.0 has some serious bugs in it.
You guys now need to roll back to v1.0.0, which is more stable.

Such a scenario is quite common when writing software,
and thanks to git, we can roll back to a stable version of our choice should
we need to.

Think of how people name their finals _Draft1_, _Draft1_final_ and eventually
_Draft_34_final_final_ultimate_.

## Getting started

### Setting up git in your local machine

### Installing git

#### Linux

Git generally comes pre-installed with Linux. You can find out by typing

```console
which git
```

If it shows you a path (most likely `/usr/bin/git`), then you have git installed.

Otherwise you can run

```console
sudo apt install git
```

If you want to download a specific version, you may be able to do so by going to
https://git-scm.com/download/linux
and following the relevant instructions.

#### Mac

Install `homebrew` first, and then type

```console
brew install git
```

### Setting up credentials

Open the terminal, and type in (with the quotes, replacing "Your Name" with
your name and the email with your email address):

```console
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
```

#### Setting up SSH for git

Type:

```console
ls ~/.ssh/id_rsa.pub
```

If you do not have an SSH key,
you will see a `ls: cannot access '~/.ssh/id_rsa.pub': No such file or directory`.
If so, type in

```console
ssh-keygen -t rsa -C "email@example.com"
```

This will generate an SSH key for you.
You can accept the defaults by pressing ENTER/Return.

Credit: [Github's guide to generating SSH key pair](https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)

After you have your SSH key, you may want to tell git host
(e.g, Github, Bitbucket) about it.

Type in:

```console
cat ~/.ssh/id_rsa.pub
```

You will see an SSH public key. That is your SSH key and one way your git host
can verify that it is indeed you.

Note: The following instructions will assume that you use Github.

Go to your Github account > Settings > SSH and GPG Keys > New SSH Key

Paste that ssh key and give it an appropriate title
that tells you which machine it is, for example “CSE Machine”, “personal-mac”, etc.

### Creating a new repository

#### Local repository

Make a new folder, `cd` into it and run `git init`. One way of doing it is:

```console
cd ~
mkdir my-repo
cd my-repo
git init
```

#### Remote repository

Create a new repository in your github account. Log in, go to your dashboard,
locate the button “New Repository”.

Fill in the name and description fields and create the repository as private.

This is where our local repository will be pushing (uploading) code to,
and pulling (downloading) code from, but we haven't told our local
repository about it yet. We will, soon.
