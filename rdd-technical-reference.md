---
title: 'SUB RDD Technical Reference'

author:
- Software Quality Working Group
...



# Purpose

This guideline should help you getting started a new software development project (or improving an existing one!) in the Research and Development Department of the Göttingen State and University Library.

Our goal is to establish better software quality by following standards the developer team has mutually agreed upon. Roughly basing on the [DARIAH Technical Reference](https://dariah-eric.github.io/technical-reference/), these standards are discussed, worked out, and decided in the Software Quality Working Group, which meets biweekly on Tuesdays at 12:30-13:30. However, they aren't cast in stone, so in case you have a good idea for a better standard, feel free to contribute!



# Status

This document is a living document and will be extended as soon as the Software Quality Working Group has agreed upon a new standard for software projects in RDD.



# Guidelines


## Do you stick to our code style guides?

### General

The basic definitions are given by our [EditorConfig](http://editorconfig.org/),
i.e. unix line breaks and 2 space indentation.

Unfortunately, not all editors support [EditorConfig](http://editorconfig.org/).
In case you use **eXide**, the IDE that comes with [exist-db](http://exist-db.org/),
you can set 2 space indentation as default by editing `/db/apps/eXide/src/preferences.js`.

### Specific for programming languagues

For the more prominent programming languages we have formatting and general style guides we ask you to follow:

- **Java**: The Java style guide can be found [here](./styles/rdd-eclipse-java-google-style.xml). It's based on the [Google style guide for Java](https://github.com/google/styleguide) with some minor RDD specific setting. You can configure Eclipse to use it automatically at *Eclipse &gt; Preferences &gt; Java &gt; Code Style &gt; Formatter*. Just load the [RDD Eclipse Java Google Style](https://raw.githubusercontent.com/subugoe/rdd-technical-reference/master/styles/rdd-eclipse-java-google-style.xml) in the formatter preferences and use it in your RDD projects.

- **JavaScript**: For JS we use the [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript). @TODO uv: How to use in editor?

- **HTML/CSS**: For HTML/CSS we agreed upon the [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.html). @TODO mw: How to use in editor?

- **XQuery**: We use the [xqdoc style guide](http://xqdoc.org/xquery-style.pdf) with the following addenda:

    - use double quotes instead of single quotes (for easy escaping) @TODO all: Discuss again with mg
    - use four spaces for a TAB (because eXide makes it so)

- **XSLT**: Since there is no official style guide for XSLT, we decided to write
[our own](https://github.com/subugoe/rdd-technical-reference/tree/master/style-guides/FE-XSLT.pdf), resulting from common best practices and own experiences within
the department.

- **SPARQL**: For SPARQL there is not really any official style guide and there is no possibility to simply include any code style automatically using a code style file. We just collect some advices how to format and use SPARQL code.

    - declaration of variables should start with a **?** (and not with a **$**).
    - **{** paranthesis should be at the end of the line. @TODO mb: Provide examples
    - group concatenations in SELECT command should be in seperate lines.


## Is your software fully documented?

### General issues

- don't document computer language's interna

- best use language structure to document

- write the best documentation you can

- documentation and variable language is American English

- should be as code-near as possible

- every code repo must have

    - a README.md file that contains @TODO mw: provide link to example
        - link to original repository
        - short introduction
        - link to demo instance
        - example or demo installation
        - link to licence file
        - contribution guide
        - link to style guide
        - link to bugtracker/project managemenmt system
        - known issues
        - badges to ci status
    - a LICENCE file

- @TODO fu: see <https://wiki.de.dariah.eu/pages/viewpage.action?pageId=64957922>

- where to document the code? where is it documented in RDD?

### Developer documentation

#### Architecture of the software

Each software project should be documented using an architecture diagram that helps understanding its basic functionality (using tools to generate diagrams such as UML class diagrams seems not to be possible in every case).

Examples:
    - @TODO mw: Looks for XQuery architecture things <https://github.com/vronk/SADE/tree/METS-crxq/docs>
    - @TODO fu: Looks for JAVA ULM things (crud?)

Call diagrams can be useful to follow code and service calls and should be existing for every API call.

#### API documentation

    - used parameters, author and since annotations
    - @TODO fu (Java): See Dennis' LABSUBBLOG entry <https://lab.sub.uni-goettingen.de/self-updating-docs.html>
    - links to callers? who is calling this method, and when?
    - @TODO mw: Test Swagger and REST API for Getty API <https://dracor.org/documentation/api/> and <https://app.swaggerhub.com/apis/swub/gdz-fulltext_api/1.0.0>

- meet and write documentation together regularly?

### Admin Documentation

- how to install the software, how to run and/or restart it, how to test the installation, ...

- server documentation

### User Documentation

- how to use the software and APIs, FAQs, walkthroughs, ...

- guided tour (Bootstrap Tour) as user documentation

    - for SADE portal usage (such as Fontane, BdN, Architrave)
    - for complex Digital Editions

- screencasts


## Which version control do you use? You do use version control, do you?

We are using GIT in RDD! Nothing else! How it works, please see <https://git-scm.com/doc>.

We recommend to use Gitflow (<@TODO mw: Link raussuchen> and <https://danielkummer.github.io/git-flow-cheatsheet>) and the protection of the develop and master branches.

Automatically closing issues via commit message depends on the Git repository server. @TODO mw: References to other issues, etcpp.

Wihch repo you are using depends on:

* the project
* existing code
* using Gitlab Runners
* ...


## Are you tracking your bugs properly?

A bug tracking system is obligatory! Please use the respective bug tracking system of your repo and/or project management solution (please see chapter version control)!

@TODO mirroring of repos for project visibility!?


## What is your test coverage?

We aim to have a test coverage of **100%** (except for getter and setter methods).
Whether you achive this by Test Driven Development (TDD) or not is specific to
yout preferred way to work.

Please keep in mind not only to write a test for each of your functions but also
to consider all possible outcomes. It is e.g. not sufficient to test if a function
creates a file if the written content depends on variables etc.

Examples for different programming languages are:

- **XQuery**: <https://gist.github.com/joewiz/fa32be80749a69fcb8da>


## Code building and continuous integration

- @TODO: Code building (such as Jenkins, Gitlab Runner)

- @TODO: Provide complete example for Jenkins and Gitlab runner!

- @TDOO: Monitoring (such as Icinga)


# Code quality level for RDD


# Licencing


# Requirements engineering


# Helpful links and references

- eurise-network technical-reference: <https://github.com/eurise-network/technical-reference>

- DHTech -- An international grass-roots community of Digital Humanities software engineers: <https://dh-tech.github.io>

- The Software Sustainability Institute, Guidelines and publicartions: <https://www.software.ac.uk>

- The Joel Test: 12 Steps to Better Code: <https://www.joelonsoftware.com/2000/08/09/the-joel-test-12-steps-to-better-code>

- Software Quality Guidelines: <https://github.com/CLARIAH/software-quality-guidelines>

- Software Testing Levels: <http://softwaretestingfundamentals.com/software-testing-levels>
