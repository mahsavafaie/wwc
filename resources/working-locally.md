# Working locally

During the sessions we have been working with ????. However, you might want to run jupyter ipython notebooks locally. This instructions will guide you to get them running in your computer and not in the cloud.

You will need `python3`, and `jupyter` at least to be able to run the notebooks. If other modules were needed, we will document it.

## python 3

Check that you have python 3 installed in your computer.

Type in the terminal:

```shell
python3 --version
```

It is installed if you get something like `Python 3.5.0`. However, if you get `python3: command not found` is very likely that you don't have python installed in your machine.

Follow this instructions to install python3.

## jupyter

Check that you have `jupyter` package for `python3` installed.

If you have the latest version of python3 in your computer, it will come with `pip`. It is a python package manager (just like `conda`) allowing you to install `jupyter` and all required dependencies.

Type in the terminal:

```shell
pip3 install jupyter
```

This procedure will install many other packages. That's just fine.

If you don't have `pip` installed in your machine, you will get an error. You will have to install it as explained [here](https://pip.pypa.io/en/stable/installing/). Or even better, install the latest `python3` version.

## packages required for notebook?

## start jupyter

Run the following command in the Terminal (Mac/Linux) or Command Prompt (Windows):

```shell
jupyter notebook
```

Two things will happen:

1. you will see some text in your terminal
1. a new tab will be open in your web browser

The text should say something like:

```
[I 19:58:53.033 NotebookApp] Serving notebooks from local directory: /Users/jmmmac
[I 19:58:53.033 NotebookApp] 0 active kernels 
[I 19:58:53.033 NotebookApp] The IPython Notebook is running at: http://localhost:8888/
[I 19:58:53.033 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
```

You should not close the Terminal/Command Prompt window until you are finished.

The new tab shows a page that should be familiar to you. You can:

1. open an existing notebook
1. create a new empty notebook

## open a notebook

Browse in the `Files` tab until you find the notebook you want to open. Click on it, and *voilà*!

## create a new notebook

Click on the right upper button called `New`, and then choose `Notebooks Python 3`.


