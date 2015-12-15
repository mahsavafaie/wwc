# Session 5: XML/HTML

In this session we provide a quick introduction to **XML** and **HTML**. We then engage with common uses of `beautifulsoup4` to read, manipulate and write XML/HTML with Python.

## XML and HTML

Both **XML** and **HTML** are markup languages. Markup languages are systems to annotate documents in a way that the annotation is syntactically distinguishable from the content. What does it mean? Well, we normally want to keep text and metatextual information separated. Metatextual information can be metadata, linguistic annotation, format, content description...

Two well known markup formats are **XML** and **HTML**. They are very similar in fact. Both are instances of SGML and both follow the DOM specification. However, **HTML** is a markup format made up of a pre-defined closed set of tags, with a specification that is used by web browsers to present web content. Whereas, **XML** is not restricted to a particular set of elements and/or purpose. Users can define the structure of the document, its elements, attributes, etc.

### HTML

**HyperText Markup Language**, commonly referred to as **HTML**, is the standard markup language used to create web pages. Web browsers can read **HTML** files and render them into visible or audible content. Since **HTML** describes the structure of the page semantically along with cues for presentation.

The language is written in the form of **HTML** elements consisting of tags enclosed in angle brackets (like `<html>`). Browsers do not display the **HTML** tags and scripts, but use them to interpret the content of the page.

The most recent version of **HTML** is `HTML5`. You have to be aware, though, that there are other specifications out there still widely used like: `HTML4` or `XHTML`.

The core components of **HTML** are: elements and their attributes, and entity references.

Elements are tags enclosed in angle brackets. Typically, tags come in pairs: a "start tag" `<p>` and "end tag" `</p>`. Although, there are also empty tags like: `<br/>`.

```xml
<a href="https://en.wikipedia.org/wiki/HTML">HTML</a>
```

<!-- go to the browser and show the source code -->

#### DOM

DOM stands for *Document Object Model*. This is the specification of how a **HTML** document has to be structured, as well as how the file is manipulated to create, edit or remove contents.

We can think of DOM as a tree structure:

![DOM Model](https://upload.wikimedia.org/wikipedia/commons/5/5a/DOM-model.svg "DOM Document Object Model")

By Birger Eriksson (Own work) [<a href="http://creativecommons.org/licenses/by-sa/3.0">CC BY-SA 3.0</a>], <a href="https://commons.wikimedia.org/wiki/File%3ADOM-model.svg">via Wikimedia Commons</a>

The equivalent **HTML** source code would look like this:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My title</title>
  </head>
  <body>
    <h1>A heading</h1>
    <a href="https://en.wikipedia.org/wiki/HTML">Link text</a>
  </body>
</html>
```

A **HTML** file normally has:

1. an **HTML** declaration `<!DOCTYPE html>`
1. an `html` element, it is the root element. The language of the document is normally specified through its attribute `lang`.
1. a `head` element, containing:
    - the `title`, and
    - `meta` elements providing information about the document like: keywords, description, author, content-type, style documents, refresh options, charset...
1. a `body` element containing what will be showed on the screen. Typical children elements are: `header`, `footer`, `div`, `p`, `br`, `h1`, `h2`...

#### Learn more about HTML

- **HTML** article in the Wikipedia <https://en.wikipedia.org/wiki/HTML>
- The Missing Link: An Introduction to Web Development and Programming <http://pressbooks.opensuny.org/themissinglink>
- w3schools.com **HTML**(5) Tutorial <http://www.w3schools.com/html>

### XML

XML sntads for EXtensible Markup Language. This language was designed to store and transport data. And it was designed to be both human- and machine-readable.

> XML is a generalized way of describing hierarchical structured data. An xml document contains one or more elements, which are delimited by start and end tags. Elements can be nested to any depth. An element inside another one is said to be a subelement or child. The first element in every xml document is called the root element. An xml document can only have one root element.

> Elements can have attributes, which are name-value pairs. Attributes are listed within the start tag of an element and separated by whitespace. Attribute names can not be repeated within an element. Attribute values must be quoted. You may use either single or double quotes.

> If an element has more than one attribute, the ordering of the attributes is not significant. An element’s attributes form an unordered set of keys and values, like a Python dictionary. There is no limit to the number of attributes you can define on each element.

> Elements can have text content. Elements that contain no text and no children are empty. Elements that contain text and children elements are said to contain mixed content.

> Finally, xml documents can contain character encoding information on the first line, before the root element.

Since XML


<!-- Complete information at least with a paragraph. -->

<!-- http://www.diveintopython3.net/xml.html -->

Learn more about **XML** with this [article](https://en.wikipedia.org/wiki/XML) from the Wikipedia, or follow the [XML Tutorial](http://www.w3schools.com/xml) from the `w3schools.com`.

### Well-formed and valid

Web browsers are quite lenient regarding not well-formed and invalid **HTML**. They will try to figure out how to render a page, even if there are errors. However, errors in **XML** documents will stop your **XML** applications. **XML** parsers will choke, **XML** errors are not allowed.

Therefore, whenever you work with markup languages, try to check that everything is alright to be sure that your material is error free. Follow this piece of advice and you will avoid lot of headache in the future.

#### Well-formed documents

A document is well-formed if it is compliant with some minimal requirements. In **HTML**:

- the document contains a document type declaration
- a single element, known as the root element, contains all the other elements in the document.
- all elements are well formed (if they are):
    - opened and subsequently closed, or
    - if empty, properly terminated, and
    - properly nested so that they do not overlap
- `<`, `>`, `"`, `'`, and `&` are only used as markup (either part of a tag or a entity). If they are to be used in the document as character, entities should be used instead: `&lt;`, `&gt;`, `&quot;`, `&apos;`, `&amp;`.
- there are rules about the characters that can be used in element names and elsewhere

The rules for well-formed **XML** go beyond the requirements mentioned above:

- tags are case-sensitive
- attribute values have to be quoted
- it contains only properly encoded legal Unicode characters

More on well-formed **XML**: <https://en.wikipedia.org/wiki/Well-formed_document>

More on well-formed **HTML**: <https://en.wikipedia.org/wiki/Well-formed_element>

#### Valid documents

**HTML** documents have to conform to a particular specification where only a closed set of elements and attributes with particular contents and data types are allowed. Try to use anything else and you will get an error.

However, the structure and contents of **XML** documents can and have to be defined. The rules describing those aspects are defined in a DTD (Document Type Definition) or **XML** schema. A document is valid if:

- it is well-formed, and
- it observes the rules dictated by its DTD or **XML** schema.

If used properly, **XML** schemas can help you to detect annotation inconsistencies and errors.

There are different ways to define documents out there. My favorite schema language is **Relax NG compact**: it is quite easy to understand, write, and read. It is much more powerful than DTDs, but easier than other **XML** schema languages.

To get started check this [tutorial](http://www.relaxng.org/compact-tutorial-20030326.html).

<!-- Add here your reference links from GECCo metadata revision -->

#### Check HTML

W3C Markup Validation Service <https://validator.w3.org/>

#### Check XML

Some **XML** editors allow the validation of **XML** files using a DTD or **XML** schema. If you have many files to validate you probably want to use a command line tool.

<!-- check the Ubuntu command -->

`jing` is the best known for Relax NG Schema compact format.
In Mac OS X you can install it with [homebrew](http://brew.sh) `brew cask install jing`. In Ubuntu there is a package called jing-trang `sudo apt-get install jing-trang`. If you are working in Windows you have to compile it from source <https://github.com/relaxng/jing-trang>.

Once it is installed, you can validate a file with something similar to:

<!-- check the syntax of the command below -->

```shell
java -jar jing.jar -c schema XMLfile
```

<!-- provide a schema and a file to validate -->

There is an online validator that you might want to try:
<https://validator.nu>

There is a python wrapper for jing-trang tools, be aware that it is still in beta: <https://pypi.python.org/pypi/jingtrang>

<!-- the python wrapper is much more interesting -->

## Python and XML/HTML

<!-- illustrate why trying to 'parse' literally or with regexp does not work -->

### Packages

Python includes different markup processing tools in its standard library.

<https://docs.python.org/3.5/library/markup.html>

- `html`, an **HTML** and **XHTML** parser.
- `xml.etree.ElementTree`, a simple and light **XML** parser, it works pretty well, it is fast and it has a pythonic API.
- `xml.dom`, a [DOM](https://en.wikipedia.org/wiki/Document_Object_Model) **XML** parser. The DOM operates on the documents as a whole.
- `xml.sax`, a [SAX](https://en.wikipedia.org/wiki/Simple_API_for_XML) **XML** parser. The SAX parser operates on each piece of the **XML** document sequentially.
- `xml.parsers.expat`, the Expat parser binding.

There are also a few packages not included in the standard library which are very useful:

- [`lxml`](http://lxml.de), which uses libxml2 and libxslt libraries. It parses **XML** and **HTML** and it is very fast. It follows the ElementTree API. Moreover, it adds interesting features like XPath, XSLT and much more.
- [`html5lib`](https://github.com/html5lib/html5lib-python), an **HTML** parser that creates valid **HTML5**, and parses pages the same browser does (extremely lenient).
- [`beautifulsoup4`](http://www.crummy.com/software/BeautifulSoup), a Python library for pulling data out of **HTML** and **XML** files. It provides idiomatic ways of navigating, searching and modifying the parse tree. You can use different parsers under the hood (like the excellent `lxml` and `html5lib`). A pythonic API.

With these last three you will get the best of Python tools to work with **HTML** and **XML**.

### Setting up the environment

We are going to use `beautifulsoup4`, `lxml` and `html5lib`. These packages are not part of python's standard library. We need to install them by using `pip`, the python package manager.

Go to the Shell Terminals in the cloud.

<!-- insert image -->

Install lxml:

```shell
sudo rpm --rebuilddb && sudo yum install -y libxml2-devel libxslt-devel && pip install lxml
```

Install html5lib:

```shell
pip install html5lib
```

Finally, install beautifulsoup:

```shell
pip install beautifulsoup4
```

> If you are working locally, the procedure to install `lxml` will be different. Check [Installing lxml](http://lxml.de/installation.html) for more information.

## Working with HTML

### Challenge



## Working with XML

### Challenge


## Summary

## Bibliography

<!-- http://www.diveintopython3.net/xml.html -->
