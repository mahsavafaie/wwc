# Working locally

During the sessions, we have been working in the cloud. However, you might want to run jupyter notebooks locally. This instructions will guide you to get them running in your computer.

You will need `python3`, `jupyter` and some additional python packages. If you try to use `python2` and the old `ipython` unexpected things will happen. Do not expect us to provide support in that case.

We will show you how to:

- get python 3 installed
- how to use virtual environments
- how to install python packages
- which packages you will need to run the notebooks of the WwC python sessions
- how to work with jupyter notebooks

In this tutorial, we are assuming that you have python3 installed in your machine, if not, follow the install instructions for Windows, Mac OS X, Ubuntu.

You can apply also this instructions in a virtual environment. Using virtual environments is a very good idea. Learn how to do it with the virtualenv tutorial.

## Python 3

Check that you have python 3 installed in your computer.

Type in the terminal:

```shell
python3 --version
```

If you get something like `Python 3.5.0`, congratulations! You have python 3 installed in your computer. However, if you get `python3: command not found`, either you don't have python 3 or your OS cannot find it.

### Installing python 3

Installing python 3 is quite easy. You can find the instructions to install the latest python 3 version in:

- Mac OS X El Capitán
<!-- - Ubuntu -->
<!-- - Windows 10 -->

The latest python 3 version comes with `pip`, a python package manager enabling the extension of your python with helpful packages, like jupyter.

If you use older versions of python3, you will have to install pip in your OS. Check `pip`'s website for further guidance. <http://pip.de>

If you try with other OS or versions, feel free to add it to this document.

#### Installing python 3 for Mac OS X

Mac OS X comes with a python 2 distribution preinstalled. You still will need python3. We recommend the software manager `homebrew` <http://brew.sh> to achieve this. You can use it to install many other tools.

1. install Xcode, Command line tools
1. install homebrew
```shell
ruby...
```
1. install python3
```shell
brew install python3
```
1. linkapps
```shell
brew linkapps python3
```
1. install yolk to keep track of your python packages (optional)
```shell
pip3 install yolk
```

#### Install python 3 for Ubuntu

Latest Ubuntu's releases come with Python 3.4 out of the box. The version can be a bit behind the latest official python 3 (3.5) release. But the notebooks should work anyway. You need to install `pip`, the python package manager.

Open a terminal and type:

```shell
sudo apt-get install python3-pip
```

<!--
#### Install python 3 for Windows 10

There are plenty of python bundles for Windows. However, we recommend you to install the latest official python 3 from the official page.

1.
1.
-->

## Python virtual environments

Virtual environments are python setups that you can manage in an isolated way and keep independent from your system python installation. If you have installed the latest python 3 following the instructions above, or you have python 3 >= 3.5, you will have `pip` installed too. Otherwise, install `pip` as explained [here](https://pip.pypa.io/en/stable/installing/).

Advantages:

- keep track of the dependencies of each project (packages and versions)
- reproducible research
- switch python versions
- test scripts for different python versions
- write code for an environment similar to the deployment

At the beginning, it might seem complicated. At the end, you will appreciate it.

### Installing virtual environments

1. install `virtualenv`
```shell
pip3 install virtualenv
```
1. install `virtualenvwrapper` (to ease `virtualenv` mangagement)
```shell
pip3 install virtualenvwrapper
```

### Setting up virtualenv and virtualenvwrapper

#### Setting up virtualenv and virtualenvwrapper for Mac OS X

This piece of code has to be added to `~/.bash_profile`.

```shell
# set where virtual environments will live
export WORKON_HOME=$HOME/.virtualenvs
# set where the location of development project directories
export PROJECT_HOME=$HOME/Devel
# ensure all new environments are isolated from the site-packages directory
export VIRTUALENVWRAPPER_VIRTUALENV_ARGS='--no-site-packages'
# use the same directory for virtualenvs as virtualenvwrapper
export PIP_VIRTUALENV_BASE=$WORKON_HOME
# makes pip detect an active virtualenv and install to it
export PIP_RESPECT_VIRTUALENV=true
if [[ -r /usr/local/bin/virtualenvwrapper.sh ]]; then
        source /usr/local/bin/virtualenvwrapper.sh
else
        echo "WARNING: Can't find virtualenvwrapper.sh"
fi
```

### Working with virtual environments

We will show you how to set up a virtual environment for WwC python sessions.

#### Create a new virtual environment

You only have to this once.

```shell
mkvirtualenv --python=/usr/local/bin/python3 wwc
```

#### Work on the new virtual environment

Whenever you want to work in a particular virtual environment, you have to activate it like this:

```shell
workon wwc
```

#### Stop working on the virtual environment

Once you are finished, or you want to switch to another virtual environment you can deactivate it:

```shell
deactivate wwc
```

## Python packages

You will need to install some packages in your `wwc` environment before you can use our notebooks. Fortunately, from python 3.5 onwards, comes with `pip` already installed.

Be sure you are working in the appropriate virtual environment:

```shell
workon wwc
```

Packages installed in a virtual environment

```shell
pip freeze
```

You will need to install the packages listed in `wwc-dependencies.txt`. Namely:

- jupyter
- pandas
- nltk
- numpy
- matplotlib

...

### jupyter

`jupyter` is a package enabling the usage of jupyter notebooks and `ipython`.

Type in the terminal:

```shell
pip3 install jupyter
```

This procedure will install `jupyter` and many other packages which are dependencies. That's just fine.

### nltk

### matplotlib

### pandas

### numpy

## Working with notebooks

We will learn in this session how to:

1. start jupyter,
1. open/create a notebook, and
1. close the notebooks and jupyter.

### Start jupyter

Run the following command in the Terminal (Mac/Linux) or Command Prompt (Windows):

```shell
jupyter notebook
```

Two things will happen:

1. you will see some text in your terminal
1. a new tab will be open in your web browser

You should not close the Terminal/Command Prompt window until you are finished.

The new tab shows a page that should be familiar to you. You can:

1. open an existing notebook
1. create a new empty notebook

### Open a notebook

Browse in the `Files` tab until you find the notebook you want to open. Click on it, and *voilà*!

### Create a new notebook

Click on the right upper button called `New`, and then choose `Notebooks Python 3`.

Click on the title and name it as you want. Or:

File -> Rename...

### Close a notebook

File -> Save and Checkpoint

File -> Close and Halt

### Stop jupyter

To stop jupyter, go to the terminal where you started it. Type twice `Control-C` to stop the server and shut down all kernels.
