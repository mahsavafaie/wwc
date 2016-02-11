# Using Git

We have used Git as version control system on GitHub to develop and share WwC materials.

> What's the point of learning this?

Well, probably you have been working on a paper or with some kind of data and you have end up with several folders, run out of ideas on how to name them, forgotten what was what, and erased accidentally that folder with the right version, or you just cannot go back to that previous version you had that was much better. If you were working with others, multiply that exponentially. Not to speak of what did who, tell the difference between two versions, etc. Git/GitHub helps you to overcome these problems and to keep track of the work done. And it is not so difficult ;-)

This tutorial will help you to set up Git on your computer and do most basic operations.

## What is Git

> Git is a widely used source code management system for software development. It is a distributed revision control system with an emphasis on speed, data integrity, and support for distributed, non-linear workflows.

> Every Git working directory is a full-fledged repository with complete history and full version-tracking capabilities, independent of network access or a central server.<sup id="a1">[1](#f1)</sup>

This means that you can set up a repository even in your laptop to work locally.

## Git/GitHub

> GitHub is a web-based Git repository hosting service. It offers all of the distributed revision control and source code management (SCM) functionality of Git as well as adding its own features. Unlike Git, which is strictly a command-line tool, GitHub provides a Web-based graphical interface and desktop as well as mobile integration. It also provides access control and several collaboration features such as bug tracking, feature requests, task management, and wikis for every project.<sup id="a1">[2](#f2)</sup>

GitHub also comes with a very complete documentation, and it has a huge community. So getting help is relatively easy. We will follow GitHub's [documentation](https://help.github.com) to get started.

## Setting up your environment

### Install Git/GitHub Desktop

To get Git working in your computer and being able to work with GitHub you need:

`if` Mac or Win:

- a [GitHub account](https://github.com/join)
- to install [GitHub Desktop](https://desktop.github.com) (if you are working with Mac/Win)

`else`:

- to install [Git](https://help.github.com/articles/set-up-git)
- a [GitHub account](https://github.com/join) (not really necessary, but helpful)

### Installing GitHub Desktop

1. Follow the instructions at the app [guide](https://help.github.com/desktop/guides/getting-started/installing-github-desktop).
1. Open the app and, you will asked for your GitHub account user and password.

That's it!

### Installing Git

To get started follow the instructions provided in GitHub's [bootcamp](https://help.github.com/articles/set-up-git).

## Creating a local repository

Say that you are working on some project and you want to use Git. You don't need to create a public repo on GitHub, but just set up one locally.

### From GUI

1. Click on the left corner `+` symbol.
1. Choose `Add`
1. Browse to the folder where you want to save your repo
1. It will ask you if you want to create a repository, provide a Name: `myfirstrepo`


### From CLI

1. Make the directory: `mkdir -p ~/myproject/myfirstrepo`
1. Change to the directory: `cd ~/myproject/myfirstrepo`
1. Start the repository: `git init`

## Create a File

1. Create a file called `README.md`
1. Write: `This is a test.`
1. Save it in your repository.

## Contributing

If you want to have a local copy of a repository in GitHub `interrogator/wwc`, and you might want to contribute to it at some point, you have to *fork* the repository. *Forking* means that you create a copy from the original, and you keep it connected.

### Fork `wwc`

The easiest way to fork a repository is:

1. log in GitHub
1. go to the URL of the repo: <https://github.com/interrogator/wwc>
1. click on `Fork`
1. a copy of the repo will be done for your user in GitHub

### Clone your fork

Clone means to creat a local copy of a remote repository. In this case we are going to clone your fork.

If you clone you can:

- have a local copy of the repo
- work locally
- synchronise the local copy with your fork (`synchronise`)
- synchronise your fork with the original (called `upstream`)
- submit pull requests (changes) to the original

#### From GUI

https://help.github.com/desktop/guides/contributing/

#### From CLI

1. copy the URL of your fork
1. write in the shell the following command

```bash
git clone https://github.com/chozelinek/wwc.git
```

## References

- Jon Dehdari's [intro](http://jon.dehdari.org/tutorials/collaboration_using_git.html)
- Pro Git [book](http://git-scm.com/book/en/v2)
- Git [documentation](http://git-scm.com/doc)
- Git [cheatsheet](https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf)
- A successful Git [branching model](http://nvie.com/posts/a-successful-git-branching-model)
- GitHub's [help](https://help.github.com)
- GitHub's [pages](https://pages.github.com)

------
<b id="f1">1</b> <https://en.wikipedia.org/wiki/Git_(software)> [↩](#a1)<br/>
<b id="f2">2</b> <https://en.wikipedia.org/wiki/GitHub> [↩](#a2)
