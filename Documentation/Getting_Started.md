# Getting Started

- [Introduction](#introduction)
- [What is Git](#what-is-git)
- [Using Git](#using-git)
- [Installation](#installation)
  - [Windows](#windows)
  - [MacOS](#macos)
  - [Linux](#linux)
- [Configuring Git](#configuring-git)
- [Outro](#outro)
- [Exercise](#exercise)

## Introduction

## What is Git

- Git is the version control system which keeps track of our files and folders into a special place called the repository, a repository is like a folder in which git keeps track of all activities which are happening into it such as modifying a file, deleting a files and so on.

- It keeps tracks of who has changed a file or folder into a repository also it details whta hanges has been made intoa repository and is there are mistakes you can revert changes back into previous form.Verson contrl sytem falls into two categories which are `centralized verson control` and `distributed version control` each has it's own prons and cons.

- Cetralized version control syetm has a central authority, there is only one repository in which each person works with that repository into a project to keep track of all activities but a major problem with centralize version control is that when a server goes offline then nobody will have an ability to work with a repository,Example of centralized version control system are subvesrion.

- Ditributed vesrion control system is the one in which inorder for multiple people to work together each person person has a copy of the repository into a a local machine and when a server goes offline nothing goes bad since everyone has a copy and when a dev wants to contribute then a he can sync and synchronize changes.

## Using Git

- There are about 3 ways to use git for version controlling.The first one is b using `command line`, the second is by using `code editors and IDE` and the last one is by using `GUI(Graphical User Interface)`,There are times when you might use coommand line for version controlling but is you want to get things fast then using command line is the best for yu and for me, On using code editors and IDE, there are many code editors and IDE, but they one which has an experience into using is VS Code which has a section for version control and you can use this shortcut into vs code to open <kbd>ctrl+ shift + G</kbd>.

- The use of git into a code editors is cool and simple but has some limitations since you can't all activities into it.By using GUI there are many GUI tools for version controlling such as Git Kraken and Source Tree.

- Into this series we will look more into using git mostly into the command line but don't worry if you don't know how to use command line.

## Installation

- Let's see on how we can install git into a machine, but before we that let's check if you have git installed into your version, open cooamd cooman prompt and type the following command.

```sh
# check git vesrion
git --version
# returns the git vesrion
```

## Windows

- Inorder to install git into windows head into git website and download git cuurent version, click into download buttona and install into your machine.Git into windows comes with git bash which is the linux environment which works into windows as emulator.

## MacOS

- Installation procedures for git into MacOS are the same but you have to choose git packages which is suitable for [MacOS]( http://git-scm.com/download/mac).

## Linux

- Installation procedures for git into Linux are the same but you have to choose git packages which is suitable for Linux.Download [here]( http://git-scm.com/download/linux).

- Installing on command line baed on linux distro.

```sh
# fedora distro
yum install git

# ubuntu distro
apt-get install git
```

## Configuring Git

- After you have installed git into your machine what follows here is configuring git into you version there are few things which we have to configure into git such as email, handling line ending, name and default editor.Aytime you push a commit into a repository, repo will have email, name to keep track of who has made those changes.

- To do that head into git terminal then use the following command which configures git global.

- Start by configuring user name, using the following cpmmand.

```sh
# configuring user name
git config --global user.name "Enter Your name Here(It should be descriptive)"
```

- Configuring git user email,confgure email which you will used for vesrion controllling.

```sh
# configuring user email
git config --global user.email "enter your email here"
```

- Configuring default editor to open for working with git, into this section I will use VS Code as the default editor.

```sh
# configuring core code editor
git config core.editor "code --await"
```

- Opening `.config` file, Inorder to edit configuration for configuration file use the following command which opens the default code editor(VS Code).

```sh
# opening code editor too see git .config file
git config --global -e
```

## Outro

- What to do when you are stuck on using git commands, There are many ways bt one of the important and easiest way is by using cooamd line terminal.

```sh
# returns the list of all git command for working with git
git help
```

- Another way is by using google or any favourite browser of your own, head into google then search any command used by git for vesrion controlling.

## Exercise
