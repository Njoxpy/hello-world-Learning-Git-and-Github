# Git Basics

- [Initializing Repository](#initializing-repository)
- [Staging Changes](#staging-changes)
- [Commiting Changes](#commiting-changes)
- [Skippig Area](#skippig-area)
- [Removing Files](#removing-files)

## Initializing Repository

- Inorder for git to keep track for all activities which are happening into repository then you need to initialize a git repository.

```sh
# create a directory
mkdir learning-git

# navigate into directory
cd learning-git

# initialize git repository
git init

# open default edotor
code .
```

- So we have followed a couple of steps for git to keep `t`rack of all` activities which` are `happening into a repo f``irst we have to create a folder` and inside a folder we have to include  files concerning about that folder, Example: Incase you` are learning web development and you want to build a project using html , CSS  and JavaScript so the folder structure will be like this you` have a folder called `Project name(todo list)` and also i`nside the folder you` have a source folder which contains the list of all files concerning you files and what is impor`tant here `is git to keep track of allactivties so inorder for git to keep track yuo have to initialize a re`pository using this command.

```sh
git init
```

## Git Workflow

- 

## Staging Changes

- So after you have made changes into a give file let's `sya you` have a file called `index.html` and into index.html you have the following code into your project.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Learning Git and Github</title>
</head>
<body>
    <div>
        <h1>Learning Git</h1>
    </div>
</body>
</html>
```

- So after we have modified index.html file the git will tell us that there are some modifications into a file called `index.html` and if you are using VS Code you will see into the source control button showing `M` showing which means modified.So inorder to see the status all files into your project we have to use `git status` command to see the status of your files for your project.

```sh
git status 
# On branch master

# No commits yet

# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#         src/

# nothing added to commit but untracked files present (use "git add" to track)
```

- By running git status returns the status of the project if git was tracking a project(if a project wa initialized) and since we have already initialized our project then we need to check status`,git returns the status that index.html file has been modfied so inorder to save those changes we use the following command.

```sh
# staging changes
git add fileName
```

- By using git add file we can list single file multiple file or we can stage all changes which are untracked at once, also we can use patterns may be want to stage all files which have `.html` extension.

```sh
# staging single file
git add fileName

# staging multiple file
git add file1 file2

# staging all changes at once, we use a period sign`
git add .

# using patterns
git add *.html
```

- but you have to be carefull wehn using `git add .` since sometimes you have large files and folders which you don't want to be tracked such as dist folders, .env file.Since I have html files`, CSS files and JavasCri`pt files I want to all at once then I will use `git add .` command to add all files at once.

```sh
git add .
```

- After all files have been added` so what is required here is using git status command to see the status of the current folder.

```sh
git status
# On branch master

# No commits yet

# Changes to be committed:
#   (use "git rm --cached <file>..." to unstage)
#         new file:   src/css/styles.css
#         new file:   src/index.html
#         new file:   src/script/script.js
```

- So after running git status we get the status of the files into a project and they do means that they are into a staging area and a green text means are into the staging area inorder, next part we gonna look into how to commit changes.

## Commiting Changes

- Inorder to commit changes into your repository in which git is intrack off then we use git commit command and -m which means a message and after that we specify a commit changes we have done into a repository for your project.

```sh
git commit -m "commit message description"

git commit -m "Initial commit"
```

- Since into my project I have set initial files for CSS, HTML and JavaScript so what to do here is including  a description about what I have done into my project,and you can use any description which desribes what you have done.There are times when you wanto to specify what changes you have meade and a commit message is to long so todo that we have to use  `git commit` command a terminal will open default editor asking to enter a commit message and description.

```sh
git commit
# [master (root-commit) 3a71eb0] initial commit
#  3 files changed, 13 insertions(+)
#  create mode 100644 src/css/styles.css
#  create mode 100644 src/index.html
#  create mode 100644 src/script/script.js
```

![Git Commit](/Assets/git%20commit%20image.PNG)

- Terminal will wait untill you `have provided  `description and after that you need close that file and terminal will terminate, so you need to add a message and description for your commit and save.

![Git commit Description](/Assets/git%20commt%20image%20description.PNG)

## Skippig Area

- You can skip staging your changes into a repository using git commit message and -a indicating all and -m for message with description.

```sh
git commit -a -m "added basic styles for CSS"
```

## Removing Files

- So what if we want to remove `index.html` file and put into a root part of the project,or what if we want to remove `styles.css` file since we don't need into our project, todo that we to use `rm` command and specify the name of the file we want to remove.

```sh
rm styles.css
```

- Inorder to see if the file has been deleted or not run git status command and you will the status of the file with `D` which means deleted.

```sh
git status -s
 D styles.css
```