# Data Carpentry with Python and NLTK

This repository contains teaching materials for Saarland Uni's [*Working With Corpora*](http://fedora.clarin-d.uni-saarland.de/unserwiki/doku.php?id=training:working_with_corpora/) program. It's been adapted from the repository for teaching materials and additional resources used by [*Research Platforms Services*](http://melbourne.resbaz.edu.au/) at the University of Melbourne to teach *Python*, *IPython*, *Jupyter* and the *Natural Language Toolkit* (*NLTK*).

Essentially, the idea of both programs is to run free training in reproducible research methods and tools via [a cloud platform](https://dit4c.github.io/), so that nobody has to worry about installation/operating system/specs problems. All code is written and executed within [Jupyter Notebooks](http://jupyter.org/), allowing easy access to earlier input and output, as well as the rich display of text/images.

Learn more on [WwC Python sessions](http://fedora.clarin-d.uni-saarland.de/unserwiki/doku.php?id=training:python) at this URL. Want to join? Register by filling in this [form](https://docs.google.com/forms/d/1VThhhXYbrcKKe8p33tijzAIpbKHBqOcVsUyEcXDAu4Y/viewform). Subscribe to the [mailing list](https://groups.google.com/forum/#!forum/workingwithcorpora) and check the [calendar](https://calendar.google.com/calendar/embed?src=toccngu71401plkr8q4ccql75s@group.calendar.google.com&ctz=Europe/Berlin) to keep up-to-date with WwC activities.

All the materials used in the workshops are in this repository. In fact, cloning this repository will be our first activity together as a group. To do that, just open your terminal and type/paste:

```shell
git clone https://github.com/interrogator/wwc.git
```

Though we'll be working with blank notebooks in our training sessions, everything we cover lives as a complete notebook in the `resources/completed-notebooks` directory. These notebooks are useful for remembering or extending what you learned in during training. Alternatively, they may be useful for those who cannot attend our sessions face-to-face.

Below is a basic overview of the sessions. You can click the headings to view complete versions of the Jupyter Notebooks we'll be using in each session. The materials are always evolving, and pull requests are always welcome.

Sessions are fairly modular, making it possible to skip particular lessons if they are not required or if time doesn't permit.

## [Orientation](https://github.com/interrogator/wwc/blob/master/resources/completed-notebooks/orientation.md)

In this session, you will learn how to use the Jupyter Notebook, as well as how to complete basic tasks with Python/NLTK. 

* Getting up and running
* What exactly are *Python*, *Jupyter* and *NLTK*?
* Introductions to *Jupyter*
* Overview of basic Python concepts: *significant whitespace*, *input/output types*, *commands and arguments*, etc.
* Introduction to NLTK
* Quickstart: *US Inaugural Addresses Corpus*
* Plot key terms in the inaugural addresses longitudinally
* Discussion: *Why might we want to use NLTK? What are its limitations?*
* Working with variables
* Writing functions
* Creating frequency distributions

## [Corpus linguistic tasks](https://github.com/interrogator/wwc/blob/master/resources/completed-notebooks/corpling.md)

In this session, we put our existing skills to work in order to investigate the corpora that come bundled with NLTK. The major kinds of processes we cover are:

* Sentence splitting
* Tokenisation
* Keywords
* n-grams
* Collocates
* Concordancing

## [Annotating data](https://github.com/interrogator/wwc/blob/master/resources/completed-notebooks/poslemma.md)

* POS tagging
* Lemmatisation
* Exploring annotated data
* Writing a concordancer

## [Regular expressions](https://github.com/interrogator/wwc/blob/master/resources/completed-notebooks/nltk-regex.md)

This lesson focusses on regular expressions, as implemented in Python.

* Introduction to the syntax
* Regular expressions in Python: `compile()`, `match()`, `findall()`, `search()`
* Regular expressions in the Shell terminal: `sed`, `grep`
* Resources around the web
  * Checkers
  * Cheatsheets
  * Crosswords

## [HTML and XML](https://github.com/interrogator/wwc/blob/master/resources/completed-notebooks/xml.md)

This session introduces HTML and XML formats, and how to manipulate them in Python.

## [File operations](https://github.com/interrogator/wwc/blob/master/resources/completed-notebooks/fileops.md)

Python can be used to manipulate local and remote files in complex ways. This session centres on the `os` and `sys` modules.

## [Wrap up](https://github.com/interrogator/wwc/blob/master/resources/completed-notebooks/wrapup.md)

Our final session involves:

* Answering important issues raised by students in earlier sessions
* Discussing local workflows:
  * How do we get everything set up on own own devices?
  * How do we get help when things go wrong?
  * How should I store/share my code?
* Brainstorming ideas for the future

## Adding to this repository

You're more than welcome to submit a pull request with changes to our course materials.

The `.ipynb` files used by both students and instructors are automatically generated using [notedown](https://github.com/aaren/notedown). Accordingly, the best way to modify our course materials is to update the `.md` file, rather than the `.ipynb` file. These also live in `resources/completed-notebooks`.

Longer functions/solutions to challenges may be archived in `resources/scripts.py`, so that they may be imported by instructors/helpers on students' notebooks if need be.
