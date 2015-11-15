---
layout: post
title:  "Setting up Windows for Ruby on Rails Development"
date:   2015-11-14 18:00:00 -0500
categories: coding ruby
---

*Lately, I've been working with a lot of folks that might want to do Ruby on Rails development, but are on Windows (instead of Mac or Linux) and don't have administrative rights. This article is for them.*

Here's how to setup Ruby on Rails on Microsoft Windows. These instructions can be performed without admin rights.

We'll be installing:

- Ruby: The programming language
- Rails: A Ruby framework/library for making web apps
- Git: Source code control
- Sublime Text: Code-savy text editor

(At time of writing, I'm using Windows 7 SP1, but this *should* work on later versions too)

## Install Ruby

We'll use [RubyInstall](http://rubyinstaller.org/downloads) to get the Ruby language installed and its common conventions/tools.

1. Download the latest installer from [RubyInstaller (link)](http://rubyinstaller.org/downloads). Do *not* get the x64 versio.
1. Run the installer
1. Install to `C:\Ruby` (or elsewhere, but remember the location)
1. Checkmark the `Add Ruby executables to Path` option
1. Open a command prompt and type `ruby -v` to verify the installation
1. Download the 32-bit Dev Kit for Ruby 2.0+ from [RubyInstaller (link)]http://rubyinstaller.org/downloads
1. After clicking the EXE, use the path to `C:\Ruby\DevKit` to extract the files
1. Run the following commands to install the Dev Kit
    1. `ruby dk.rb init`
    1. `ruby dk.rb install`

## Install Rails

This will install Rails, the Ruby library/framework for making web applications.

1. Open a command prompt
1. Run: `gem install rails`
1. To verify: `rails -v`

## Install Git

If you're working on a Rails projects, odds are good that you'll be using Git or GitHub for getting or storing your code.

1. Download the latest installer from [Git's site](https://git-scm.com)
1. Open the installer, and proceed through all prompts with defaults, except for:
    - Installation directory: `C:\git`
    - Adjusting your PATH environment: `Use Git and optional Unix tools from the Windows Command Prompt`
    - Configuring the line ending conversions: `Checkout as-is, commit Unix-style line endings`
1. After completing the install, go to your Start menu and click the *Git Bash* application
1. At the prompt, enter the following commands (with your info) to get setup:
    1. `git config --global user.name "(your name)"`
    1. `git config --global user.email "(your email)"`

If you're new to Git, definitely checkout [GitHub's graphical Desktop application](https://desktop.github.com) (which is much easier to use).

## Configure GitHub Account

Speaking of GitHub, GitHub is the most popular site for source code repositories on the Internet and many open source projects use it. To get setup for this:

1. Create an account at [GitHub](https://github.com)
1. Open a *Git Bash* terminal
1. Run this command to generate a security/SSH key, accepting the default file name by hitting *Enter* (but enter a good password when prompted): `ssh-keygen -t rsa -b 4096 -C "(your email)"`
1. Run the SSH Agent: `eval $(ssh-agent -s)`
1. Add your SSH key: `ssh-add ~/.ssh/id_rsa`
1. Copy the key to the clipboard: `clip < ~/.ssh/id_rsa`
1. Add the key to your GitHub account (the *Title* can be anything, the *Key* is the pasted contents of `~/.ssh/id_rsa`)

## Install Sublime Text

Sublime Text is a popular text editor that opens Ruby files with pretty coloring. :-)

1. Go to the [Sublime Text Download page](http://www.sublimetext.com/2)
1. Download the portable version for Windows (this will download a ZIP file)
1. Extract the ZIP file to `C:\sublime`
1. To launch the editor, open `C:\sublime\sublime_text.exe`

Tip: `File > Open Folder` is a great way to open an entire Ruby on Rails project for editing.

## Other Notes

- Typically it is a good idea to build applications in isolation by controlling which Gems are installed. Version managers such as **rbenv** or **rvm** are used in the Mac and Linux worlds, both for this, but also to make it easy to get and upgrade to new versions. Unfortunately, Windows's most popular version manager is Pik, but has been discontinued since 2012. [Uru](https://bitbucket.org/jonforums/uru) is what the Pik creator suggests, but I haven't used it
