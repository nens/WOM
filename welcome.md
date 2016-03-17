# Welcome to our office
Do you really want to be a software developer? It means painstaking hours of staring at commas, indentation and semicolons only to find out you've made a small typo. 

This guide covers a few topics:
* [Introduction](#introduction)
* [Tools](#tools)
* [Learning JavaScript](#learning-javascript)
* [Learning Python](#python)


# Introduction
Here at Nelen & Schuurmans we use a number of tools and language that we deem a good fit for our company, namely: Python and JavaScript.

Why? The list of things you can do with Python/JavaScript is endless:

* Make web applications: Py [Flask](https://flask.pocoo.org), JS [hapi.js](hapijs.com)
* Make desktop software: JS [Electron](http://electron.atom.io/), Py [GTK](http://python-gtk-3-tutorial.readthedocs.org/en/latest/)
* Program hardware: Py [MicroPython](https://micropython.org/), JS [Tessel](https://tessel.io)
* Data visualization: JS [D3.js](https://d3js.org/), Py [Matplotlib](http://matplotlib.org/)
* Geographical programming: Py [GDAl](https://pypi.python.org/pypi/GDAL/), JS [Turf](https://turfjs.orgi)
* Make games: JS [Phaser](http://phaser.io/), Py [PyGame](http://pygame.org/hifi.html)
* 3D programming: JS [Three.js](http://threejs.org/), Py [Pyglet](https://bitbucket.org/pyglet/pyglet/wiki/Home) 

The main reason for choosing these languages is that we like code that is easy to read and to maintain, and we like developer productivity. Python also finds very broad support on geographical analysis, which is core to our organization.
JavaScript is just: inevitable. It runs everywhere, and what you make becomes very portable. Most devices people use daily have a powerful JavaScript engine running: the Browser. The browser, Firefox, Chrome, Edge, supports a number of things out of the box that don't come so easily when you're working on other platforms.

# Tools
Software developers as a rule are very particular about what kind of tools they like to use. And that makes perfect sense. Software development is a very nasty business if we didn't use software to make it easier to write software. Regardless of what type of programmer you will need to use:

* [a decent editor](#decent-editor)
* [version control](#version-control)
* [package manager](#package-manager)
* [test suite](#test-suite)

## Decent editor
Some say they cannot do without an IDE and some like their editor a bit more barebones. Then there is always a small amount of people who couldn't care less (@bertonens) about what kind of editor they use, as long is isn't slow.

Editors you can use when doing Python/JavaScript in alphabetical order:
* [Atom](https://atom.io/) - Atom is open source and free to use and hack on
* `emacs` - is an open source command line text editor 
* [PyCharm](https://www.jetbrains.com/pycharm/) - PyCharm has a free version, but you want the paid one
* [Sublime Text](https://www.sublimetext.com/) - Sublime is free to try
* `vim` - is an open source command line text editor 
* [Visual Studio Code](https://code.visualstudio.com/) - VS Code is open source and free to use and hack on

Get to know your editor of choice well. Use a cheatsheet to get acquainted with some tools it has. Look for a linter you like (a thing that checks if your code is nice and orderly), this will save you a ton of time.

### Command line editors
Command line editors are editors you can use from the terminal, locally or on the server. The above mentioned `vim` or `emacs` usually come pre-installed on most \*nix Operating Systems. If you really don't like using that on a server you can also use `nano`.

## Package Manager
Both platforms make it easy to maintain and release software without the need to download seperate packages, but using a package manager.

JavaScript's defacto package manager is excellent and called [npm](https://npmjs.com). It is the largest collection language-specific software in the world and is packaged with [node](https://nodejs.org).

Python uses [pip](https://pip.pypa.io/en/stable/installing/). You can use it in conjunction with virtualenvwrapper, which is a tool to seperate your packages important to your project from the rest of your system.

# Learning JavaScript
JavaScript has a superpower that no other language can compete with: it runs in every browser. Which means you can start learning right away without even downloading extra stuff.
The other superpower JavaScript has is that it is slowly taking over the world. Almost anything you can think of has also been written for, ported to, or conceived in JavaScript, which is congruent with [Atwood's Law](http://blog.codinghorror.com/the-principle-of-least-power/). JavaScript does not only run in the browser, but you can also run JavaScript as a server side application or make it do a ton of crazy stuff with [node.js](https://nodejs.org/en/).

## Mozilla articles
Mozilla is the foundation behind the Firefox browser, they have an excellent set of documents on a big range of topics. Let's highlight a few:
* [Introduction to HTML](https://developer.mozilla.org/en-US/Learn/HTML/Introduction_to_HTML)
* [Introduction to CSS](https://developer.mozilla.org/en-US/Learn/CSS/Introduction_to_CSS)
* [Introductory JavaScript](https://developer.mozilla.org/en-US/Learn/Getting_started_with_the_web/JavaScript_basics)
* [Intermediate JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)
* [Advanced JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
* The JavaScript Guide for programmers: [MDN JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/)

## Frontend Development
We dipped our toes in JavaScript a bit, and we've played with it in the browser. Now what? Well, what kind of software are you writing. In the first section I said web applications can be made with [hapi.js](https://hapijs.com). While this is true that is not the case here at Nelen & Schuurmans. Most of the web application's backend is written in Django. The frontend is a whole different ball game. And something you can't really do properly while using Python. (Yes, I said it.)

The frontend is a difficult thing to work on, because it *almost requires* you to keep track of more than just JavaScript. It is combination of Markup with HTML, Styling with CSS and the Logic in JavaScript. But since this paragraph is about JavaScript let's just focus on JavaScript and how it interacts with the markup of a page.

There are a number of frontend frameworks that help you do this. 
* [Angular](https://angularjs.org)
* [Backbone](https://backbonejs.org)
* [Ember](http://emberjs.com/)

Most of our big projects are in Angular. So take that for a spin. Go to the website and try the tutorials (for Angular 1.x)

The same goes for setting up a layout and a structure in your HTML and getting a battery pack for your CSS:
* [Bootstrap](http://getbootstrap.com/)
* [Foundation](http://foundation.zurb.com/)
* [yeti.css](http://yeticss.com/)

If you're ready to dive deeper in to JavaScript take a look at these websites containing a bunch of solid articles:
* [Superhero.js](http://superherojs.com/)
* [Essential Javascript Links](https://github.com/ericelliott/essential-javascript-links)

# Learning Python
At our office we use Python and the Django Web framework with Django Rest Framework, to create smooth running web applications that can handle all kinds of data. 

* [the Django web framework](http://djangoproject.com). Which is really great if you'd like to make an application for the web
* main scripting language in graphics software like Houdini or [Blender](http://blender.org)
* machine learning, data science and that type of stuff with [NumPy/SciPy](NumPy/SciPy) and [scikit-learn](http://scikit-learn.org/)

## Tutorials
A good place to start is the Python tutorial by Zed Shaw called: [Learn Python the Hard Way](http://learnpythonthehardway.org/)
If you feel you are getting the hang of it, I recommend trying out the excellent [Django tutorial](https://docs.djangoproject.com/en/1.9/intro/)

## Dig deep
If you really want to dig deeper and look at different use cases, I recommend checking out @kennethreitz' [Hitchhiker's Guide to Python](http://docs.python-guide.org/en/latest/)


# Author & Licensing
@fritzvd wrote this under company time for @nelenschuurmans.

This document is Licensed under a permissive MIT license.
