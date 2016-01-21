# Session 5: XML

In this session we provide a quick introduction to **XML**. We then engage with common uses of `beautifulsoup4` to read, manipulate and write XML data with Python.

## XML and HTML

Both **XML** and **HTML** are markup languages. Markup languages are systems to annotate documents in a way that the annotation is syntactically distinguishable from the content. What does it mean? Well, we normally want to keep text and metatextual information separated. Metatextual information can be metadata, linguistic annotation, format, content description...

Two well known markup formats are **XML** and **HTML**. They are very similar in fact. Both are instances of SGML and both follow the DOM specification. However, **HTML** is a markup format made up of a pre-defined closed set of tags, with a specification that is used by web browsers to present web content. Whereas, **XML** is not restricted to a particular set of elements and/or purpose. Users can define the structure of the document, its elements, attributes, etc.

Because most of what we will learn for XML also applies to HTML (we can regard HTML as a specification of the more general XML), and there are plenty of resources in the web to learn HTML, we will focus on XML.

### Documents as trees

DOM stands for *Document Object Model*. This is the specification of how a **HTML** and **XML** documents has to be structured, as well as how the file is manipulated to create, edit or remove contents.

We can think of DOM as a tree structure:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<TextCorpus lang="de">
    <text>Karin fliegt nach New York. Sie will dort Urlaub machen.</text>
    <tokens>
        <token ID="t_0">Karin</token>
        <token ID="t_1">fliegt</token>
        <token ID="t_2">nach</token>
        <token ID="t_3">New</token>
        <token ID="t_4">York</token>
        <token ID="t_5">.</token>
        <token ID="t_6">Sie</token>
        <token ID="t_7">will</token>
        <token ID="t_8">dort</token>
        <token ID="t_9">Urlaub</token>
        <token ID="t_10">machen</token>
        <token ID="t_11">.</token>
    </tokens>
</TextCorpus>
```

### XML

**XML** stands for E**X**tensible **M**arkup **L**anguage. This language was designed to store and transport data. And it was designed to be both human- and machine-readable. Unlike HTML the structure of the document, the elements, their attributes, and the content are not pre-defined. That provides a very flexible framework.

> XML is a generalized way of describing hierarchical structured data. An XML document contains one or more **elements**, which are delimited by **start** and **end** **tags**.

```xml
<s>This is a sentence.</s>
```

> Elements can be nested to any depth. An element inside another one is said to be a subelement or **child**. The first element in every XML document is called the **root** element. An XML document can only have one root element.

```xml
<s>
    <token>This</token>
    <token>is</token>
    <token>a</token>
    <token>sentence</token>
    <token>.</token>
</s>
```
> Elements can have **attributes**, which are name-value pairs. Attributes are listed within the start tag of an element and separated by whitespace. Attribute names can not be repeated within an element. Attribute values must be quoted. You may use either single or double quotes.

```xml
<s id="s_0">
    <token pos1="DT" pos2="DET">This</token>
    <token pos1="VBZ" pos2="VERB">is</token>
    <token pos1='DT' pos2='DET'>a</token>
    <token pos1='NN' pos2='NOUN'>sentence</token>
    <token pos1='.' pos2='PUNCT'>.</token>
</s>
```

> If an element has more than one attribute, the ordering of the attributes is not significant. Element’s attributes form an unordered set of keys and values, like a Python dictionary. There is no limit to the number of attributes you can define on each element.

```xml
<s id="s_0">
    <token pos1="DT" pos2="DET">This</token>
    <token pos2="VERB" pos1="VBZ">is</token>
    <token pos1="DT" pos2="DET">a</token>
    <token pos2="NOUN" pos1="NN">sentence</token>
    <token pos1="." pos2="PUNCT">.</token>
</s>
```

> Elements can have **text content**. Elements that contain no text and no children are **empty**. Elements that contain text and children elements are said to contain **mixed content**.

This is an element with text content:

```xml
<s>This is a sentence.</s>
```

This is an empty element:

```xml
<comment type="gesture"/>
```

This is an element with mixed content:

```xml
<s>This is a sentence with <italics>mixed</italics> content.</s>
```

> Finally, XML documents can contain character encoding information on the first line, before the root element.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<s>
    <token>This</token>
    <token>is</token>
    <token>a</token>
    <token>sentence</token>
    <token>.</token>
</s>
```

(Mark Pilgrim. *Dive Into Python 3*. <http://www.diveintopython3.net/xml.html>)

### Well-formed and valid

Web browsers are quite lenient regarding not well-formed and invalid **HTML**. They will try to figure out how to render a page, even if there are errors. However, errors in **XML** documents will stop your **XML** applications. **XML** parsers will choke, **XML** errors are not allowed.

Therefore, whenever you work with markup languages, try to check that everything is alright to be sure that your material is error free. Follow this piece of advice and you will avoid lot of headache in the future.

#### Well-formed documents

A document is well-formed if it is compliant with some minimal requirements:

- the document contains a document type declaration
- a single element, known as the root element, contains all the other elements in the document.
- all elements are well formed (if they are):
    - opened and subsequently closed, or
    - if empty, properly terminated, and
    - properly nested so that they do not overlap
- `<`, `>`, `"`, `'`, and `&` are only used as markup (either part of a tag or a entity). If they are to be used in the document as character, entities should be used instead: `&lt;`, `&gt;`, `&quot;`, `&apos;`, `&amp;`.
- there are rules about the characters that can be used in element names and elsewhere
- tags are case-sensitive
- attribute values have to be quoted
- it contains only properly encoded legal Unicode characters

<!-- look for an online validator, HTML is also OK for this purpose -->

#### Valid documents

**HTML** documents have to conform to a particular specification where only a closed set of elements and attributes with particular contents and data types are allowed. Try to use anything else and you will get an error.

However, the structure and contents of **XML** documents can and have to be defined. The rules describing those aspects are defined in a DTD (Document Type Definition) or **XML** schema. A document is valid if:

- it is well-formed, and
- it observes the rules dictated by its DTD or **XML** schema.

If used properly, **XML** schemas can help you to detect annotation inconsistencies and errors (specially helpful if you are working with data created manually by humans).

There are different ways to define documents out there. My favorite schema language is **Relax NG compact**: it is quite easy to understand, write, and read. It is much more powerful than DTDs, but at the same time easier than other **XML** schema languages.

<!-- show a DTD example and a Relax NG compact schema -->

Learning the basics of writing a DTD or a schema would require a dedicated session.

#### Validating XML

Some **XML** editors allow the validation of **XML** files using a DTD or **XML** schema.

<!-- provide the a XML file with its rnc -->

<!-- just work with the TCF Validator, to illustrate the point will be enough https://weblicht.sfs.uni-tuebingen.de/tcf-validator/ -->

If you have many files to validate, you probably want to use a command line tool like `xmllint`. It is included in [`libxml2`](<http://www.xmlsoft.org/downloads.html>). A library that you would need anyway, if you want to work with `lxml` package locally.

If you work with Relax NG Schema compact, you can use [`jing`](<https://github.com/relaxng/jing-trang>). There is also a python wrapper for jing-trang tools <https://pypi.python.org/pypi/jingtrang>.

## Python and XML/HTML

<!-- illustrate why trying to 'parse' literally or with regexp does not work: indentation, context, attribute order, attribute ambiguity... -->

### Packages

Python includes different markup processing tools in its standard library.

<https://docs.python.org/3.5/library/markup.html>

- `html`, an **HTML** and **XHTML** parser.
- `xml.etree.ElementTree`, a simple and light **XML** parser, it works pretty well, it is fast and it has a pythonic API.
- `xml.dom`, a [DOM](https://en.wikipedia.org/wiki/Document_Object_Model) **XML** parser. The DOM operates on the documents as a whole.
- `xml.sax`, a [SAX](https://en.wikipedia.org/wiki/Simple_API_for_XML) **XML** parser. The SAX parser operates on each piece of the **XML** document sequentially.
- `xml.parsers.expat`, the Expat parser binding.

There are also a few packages not included in the standard library which are very useful:

- [`lxml`](http://lxml.de), which uses `libxml2` and `libxslt` libraries. It parses **XML** and **HTML** and it is very fast. It follows the ElementTree API. Moreover, it adds interesting features like `XPath`, `XSLT` and much more.
- [`html5lib`](https://github.com/html5lib/html5lib-python), an **HTML** parser that creates valid **HTML5**, and parses pages like a browser does (extremely lenient).
- [`beautifulsoup4`](http://www.crummy.com/software/BeautifulSoup), a Python library for pulling data out of **HTML** and **XML** files. It provides idiomatic ways of navigating, searching and modifying the parse tree. You can use different parsers under the hood (like the excellent `lxml` and `html5lib`). You just learn one API and you use it for all the parsers.

### Setting up the environment

We are going to use `lxml` and `beautifulsoup4`. These packages are not part of python's standard library. We need to install them by using `pip`, the python package manager.

Go to the Shell Terminals in the cloud.

Install `lxml`:

```shell
sudo rpm --rebuilddb && sudo yum install -y libxml2-devel libxslt-devel && pip install lxml
```

Then, install `beautifulsoup4`:

```shell
pip install beautifulsoup4
```

> If you are working locally, the procedure to install `lxml` will be different. Check [Installing lxml](http://lxml.de/installation.html) for more information.

## Working with XML

### Read XML from a string

<!-- @instructor: tweak the XML input to show different errors, and how the errors break the script. Examples:

- add a second root element
- remove a closing tag
- change an opening token tag to taken
- remove the quotation marks of an attribute
- write an element hows tag starts by an invalid character
- insert a sentence element wrong
- insert sentence elements right
- insert an ampersand
- use the ampersand entity
- put opening tag in upper case, and leave closing tag in lowercase
-->

```python
from bs4 import BeautifulSoup

xmlsource = '''<?xml version="1.0" encoding="UTF-8"?>
<TextCorpus lang="de">
    <text>Karin fliegt nach New York. Sie will dort Urlaub machen.</text>
    <tokens>
        <token ID="t_0">Karin</token>
        <token ID="t_1">fliegt</token>
        <token ID="t_2">nach</token>
        <token ID="t_3">New</token>
        <token ID="t_4">York</token>
        <token ID="t_5">.</token>
        <token ID="t_6">Sie</token>
        <token ID="t_7">will</token>
        <token ID="t_8">dort</token>
        <token ID="t_9">Urlaub</token>
        <token ID="t_10">machen</token>
        <token ID="t_11">.</token>
    </tokens>
</TextCorpus>'''

soup = BeautifulSoup(xmlsource, 'xml')

print(soup.prettify())
```

Cool! That's nice. Let's get familiar with our soup.

### Common operations

#### The basics

Elements are `Tag` objects.

Get the tokens element.

```python
soup.tokens
```

Get a token element just by using the element name:

```python
atoken = soup.token
```

Every tag has a `name`:

```python
atoken.name
```

A tag may have attributes or `attrs`. Attributes are like a dictionary:

```python
atoken.attrs
```

```python
atoken['ID']
```

A tag can contain text or `string`. This content is seen as a unicode string.

<!-- but this only works for text content, with mixed content it doesn't -->

```python
atoken.string
```

A tag has `contents`, which is the same as a list of text and/or children.

```python
soup.tokens.contents
```

#### Finding things

Find elements using a string

```python
all_tokens = soup.find_all('token')
```

Find elements using a regexp

```python
import re
for tag in soup.find_all(re.compile("^text")):
    print(tag.name)
```

Find elements considering an attribute:
```python
soup.find_all('token',ID="t_1")
soup.find_all('token',ID=re.compile('^t_1'))
```

Find elements using a list

```python
soup.find_all(['text','token'])
```

Get all tags in a document

```python
for tag in soup.find_all(True):
    print(tag.name)
```

Find a particular string:

```python
soup.find_all('token', string="Urlaub")
```

To find just one, use `find`:

```python
soup.find('token')
soup.find_all('token')
```

#### Finding members of the family

With `find_all` we find all the descendants.

Get only direct children

```python
soup.find_all(True,recursive=False)
```

Get the parent and ancestors of an element

```python
token = soup.find('token')
token.find_parent(True)
token.find_parents(True)
```

Get the siblings

```python
next_token = token.find_next_sibling()
next_token
token.find_next_siblings()
next_token.find_previous_sibling()
```

Get all siblings

```python
for sibling in soup.token.next_siblings:
    print(sibling)
for sibling in soup.token.find(ID="t_3").previous_siblings:
    print(sibling)
```

### Read a XML file

```python
soup = BeautifulSoup(open('../../tcf04-karin-wl.xml', 'r', encoding='utf-8'), 'xml')



```

### Extracting Info

### Challenges

- reconstruct the text from `tokens`, so `text == tokens`
- find all nouns, print the POS tag
- find all nouns, retrieve word forms, print the text of the token
- find all nouns, check condition, retrieve POS tag of previous token


### Manipulating XML

upper case all tokens


add lemmas to tokens





### Challenge

```
soup = BeautifulSoup(open('tcf04-karin-wl.xml', 'r', encoding='utf-8'), 'xml')
```

- lower case all tokens
- change the `tag` 'ID' value, by changing the prefix. Instead of `pt` now should be `postag`.
- add `length` in characters to `token`
- add `length` in tokens to `sentence`
- for each `token` add an attribute called `pos` which should be its value from `tag`.
- renumber tokens, instead of starting at `0` they should start at `1`
- remove elements
- strip tags

### Creating an XML file

### Challenge

- convert VRT file into XML (tokens with attributes)
- convert VRT file into XML (tokens with attributes and IDs)
- convert VRT file into XML (sentences with IDs, tokens with attributes and IDs)
- convert VRT file into XML (sentences with IDs and lenght in tokens, tokens with attributes and IDs)

## Summary

## Learn more

After having learnt a bit of **XML** and `beautifulsoup4`, you are ready to learn on your own about **HTML** and web scrapping.

### HTML

Learn more about HTML:

- **HTML** article in the Wikipedia <https://en.wikipedia.org/wiki/HTML>
- The Missing Link: An Introduction to Web Development and Programming <http://pressbooks.opensuny.org/themissinglink>
- w3schools.com **HTML**(5) Tutorial <http://www.w3schools.com/html>

### Web scrapping with `beautifulsoup4`

- <http://web.stanford.edu/~zlotnick/TextAsData/Web_Scraping_with_Beautiful_Soup.html>
- <http://programminghistorian.org/lessons/intro-to-beautiful-soup>

### XML

We have just scratched the surface today. If you want to learn more, you can start here:

- **XML** article in the Wikipedia <https://en.wikipedia.org/wiki/XML>
- w3schools.com **XML** tutorial <http://www.w3schools.com/xml/default.asp>

### Relax NG compact

Check this tutorial to get started: <http://www.relaxng.org/compact-tutorial-20030326.html>

To validate XML files using this schema format you can use `jing`.

You can also install `jing` directly without the python wrapper. In Mac OS X you can install it with [homebrew](http://brew.sh) `brew cask install jing`. In Ubuntu there is a package called jing-trang `sudo apt-get install jing-trang`. If you are working in Windows you have to compile it from source <https://github.com/relaxng/jing-trang>.

To validate an XML file you use the following command:

```shell
jing -c schema.rnc file.xml
```

If the file is valid, you won't get any message. If there is something wrong, you will some.

There is also a python wrapper. No need to install `jing` and `trang` on your own, but you need `java` to be installed in your computer.

You can install it through `pip`:

```shell
pip install jingtrang
```

To validate an XML file against a Relax NG compact schema run the following command:

```shell
pyjing -c schema.rnc file.xml
```

### lxml

If you need better performance and/or you need higher control of what the parser does. Or you are familiar with XPath, and XSLT you might want to give a try to `lxml`.

<http://lxml.de/tutorial.html>

Check [Installing lxml](http://lxml.de/installation.html) for more information. Be aware that `lxml` requires `libxml2` and `libxslt`. [`libxml2`](<http://www.xmlsoft.org/downloads.html>).

If they are not installed in your machine, you will have to install them. In Mac OS X you can install it with [homebrew](http://brew.sh) `brew install libxml2 libxslt`. In Ubuntu there is a package called jing-trang `sudo apt-get install libxml2-dev libxslt1-dev`. If you are working in Windows you have to follow the instructions provided by [Igor Zlatkovic](https://www.zlatkovic.com/libxml.en.html).

## Bibliography

<!-- http://www.diveintopython3.net/xml.html -->
