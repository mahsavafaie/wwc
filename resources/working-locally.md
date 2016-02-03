# Working locally

During the sessions, we have been working in the cloud. However, you might want to run jupyter notebooks locally. This instructions will guide you to get them running in your computer.

You will need `python3`, `jupyter` and some additional python packages. If you try to use `python2` and the old `ipython` unexpected things will happen.

We will show you how to:

- get python 3 installed
- how to use virtual environments
- how to install python packages
- which packages you will need to run the notebooks of the WwC python sessions
- how to work with jupyter notebooks

The instructions have been tested for Mac OS X 10.11 El Capitan, Ubuntu 15.10 Wily Werewolf, and Windows 10.

## Python 3

The first question we need to answer is:

> Do I have python 3?

You can open a Terminal or Console and type the following command:

```shell
python3 --version
```

If you get something like `Python 3.5.0`, congratulations! You have python 3 installed in your computer. However, if you get `python3: command not found`, either you don't have python 3 or your OS cannot find it.

If you DO have python 3 already installed in your machine, check the version you have. If the version is >= than 3.4. proceed to section [Python virtual environments](#python-virtual-environments), otherwise, you will need to install pip, go to section [Installing pip](#installing-pip). If you DO NOT have python 3 installed in your computer follow the instructions in section [Installing python 3](#installing-python-3).


## Installing python 3

Depending on the platform you are working, you will need to follow a different procedure:

- [Mac OS X](#installing-python-3-for-mac-os-x)
- [Ubuntu](#installing-python-3-for-ubuntu)
- [Windows](#installing-python-3-for-windows)

### Installing python 3 for Mac OS X

Mac OS X comes with a python 2 distribution preinstalled. You still will need python 3. We will use in this tutorial the software manager `homebrew` <http://brew.sh>.

1. install Command Line Tools for Xcode
```shell
xcode-select --install
```
1. install homebrew
```shell
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
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

Now, you check again if python 3 is installed by running:

```shell
python3 --version
```

You should see `Python 3.5.0`.

If you were successful go to section [Python virtual environments](#python-virtual-environments).

### Installing python 3 for Ubuntu

Congratulations! Latest Ubuntu's releases come with Python 3.4 out of the box. The version can be a bit behind the latest official python 3 (3.5) release. But the notebooks should work anyway. You need to install `pip`, the python package manager.

Go to [Installing pip](#installing-pip).

### Installing python 3 for Windows

## Installing pip

Check if you already have `pip3` installed running the command below:

```shell
pip3 --version
```

If you DO have `pip3` installed go to section [Python virtual environments](#python-virtual-environments).
If you DO NOT have `pip3` follow this instructions: <http://pip.de>

### Installing pip for Mac OS X

If you followed the instructions to install python 3 with homebrew you don't need to install pip. The latest versions come with pip already.

### Installing pip for Ubuntu

Open a terminal and type:

```shell
sudo apt-get install python3-pip
```

Check again if you already have `pip3` installed running the command below:

```shell
pip3 --version
```

### Installing pip for Windows


## Python virtual environments

We recommend you to work with python virtual environments. If you don't want to use virtual environments go to section [Installing python packages](#installing-python-packages), just remember to use `pip3` command instead of just `pip`.

**What are virtual environments?** Virtual environments are python setups that you can manage in an isolated way and keep independent from your system python installation. If you have installed the latest python 3 following the instructions above, or you have python 3 >= 3.5, you will have `pip` installed too. Otherwise, install `pip` as explained in section [Installing pip](#installing-pip).

Advantages:

- keep track of the dependencies of each project (packages and versions)
- reproducible research
- switch python versions
- test scripts for different python versions
- write code for an environment similar to the deployment

At the beginning, it might seem complicated. At the end, you will appreciate it.

### Installing virtual environments

<!-- this commands work for mac and lin -->

1. install `virtualenv`
```shell
pip3 install virtualenv
```
1. install `virtualenvwrapper` (to ease `virtualenv` mangagement)
```shell
pip3 install virtualenvwrapper
```

The next step is to set up `virtualenv` and `virtualenvwrapper`.

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

#### Setting up virtualenv and virtualenvwrapper for Ubuntu

Open a terminal window, and run the following commands:

```shell
sudo apt-get install virtualenv
sudo apt-get install virtualenvwrapper
source .bashrc
```

#### Setting up virtualenv and virtualenvwrapper for Windows

### Working with virtual environments

We will show you how to set up a virtual environment for WwC python sessions.

#### Create a new virtual environment

You only have to this once.

```shell
mkvirtualenv --python=$(which python3) wwc
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

### Installing python packages for Mac OS X


You will need to install some packages in your `wwc` environment before you can use our notebooks.

Be sure you are working in the appropriate virtual environment:

```shell
workon wwc
```

If you prefer not to work with virtual environments just follow the instructions below.

Packages installed in a virtual environment

```shell
pip3 freeze
```

You will need to install the packages listed in `wwc-dependencies.txt`. Namely:

- jupyter
- pandas
- nltk
- numpy
- matplotlib

...

#### jupyter

`jupyter` is a package enabling the usage of jupyter notebooks and `ipython`.

Type in the terminal:

```shell
pip3 install jupyter
```

This procedure will install `jupyter` and many other packages which are dependencies. That's just fine.

#### nltk

```shell
pip3 install nltk
```

#### matplotlib

```shell
pip3 install matplotlib
```

#### pandas

```shell
pip3 install pandas
```

#### numpy

```shell
pip3 install numpy
```

### Installing python packages for Ubuntu

### Installing python packages for Windows


## Working with jupyter notebooks

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
