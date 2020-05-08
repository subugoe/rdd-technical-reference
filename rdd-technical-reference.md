---
title:  'SUB RDD Technical Reference'
...


# About this Document

**Author**: Software Quality Working Group\
\
**Audience**: Developers of the Research and Development Department of the Göttingen State and University Library.
\
**Purpose**: This guideline should help you getting started a new software development project (or improving an existing one!) in the Research and Development Department of the Göttingen State and University Library.

Our goal is to establish better software quality by following standards the developer team has mutually agreed upon. Roughly basing on the [EURISE Network Technical Reference](https://eurise-network.github.io/), these standards are discussed, worked out, and decided in the Software Quality Working Group, which meets biweekly on Tuesdays at 13:00--14:00. However, they aren't cast in stone, so in case you have a good idea for a better standard, feel free to contribute!\
\
**Status**: This document is a living document and will be extended as soon as the Software Quality Working Group has agreed upon a new standard for software projects in RDD.
TODOs and addenda of this document are maintained [here](https://github.com/subugoe/rdd-technical-reference/issues/).


# Explanatory Notes

**CESSDA's Software Maturity Levels (SML)**: Several organizations already have put a lot of work into developing metrics for good software. Since we didn't want to reinvent the wheel, we decided to adapt (and modify if need be) a metric which suits our needs. [CESSDA](https://www.cessda.eu/) is one of the ERICs, and although it focuses on Social Sciences it has similar requirements regarding its software.

Throughout the document you will find sections with the heading "CESSDA's Software Maturity Levels in RDD" in which we describe which of the SMLs we aim for and how we want to implement it.


# Style Guides

## General

The basic definitions are given by our [EditorConfig](http://editorconfig.org/) file, `.editorconfig`,
i.e. Unix line breaks and 2 space indentation.

## Specific for Programming Languages

For the more prominent programming languages we have formatting and general style guides we ask you to follow:

- **Java**: The Java style guide can be found [here](./styles/rdd-eclipse-java-google-style.xml). It's based on the [Google style guide for Java](https://github.com/google/styleguide) with some minor RDD specific settings. You can configure Eclipse to use it automatically at *Eclipse &gt; Preferences &gt; Java &gt; Code Style &gt; Formatter*. Just load the [RDD Eclipse Java Google Style](https://raw.githubusercontent.com/subugoe/rdd-technical-reference/master/styles/rdd-eclipse-java-google-style.xml) in the formatter preferences and use it in your RDD projects.

- **JavaScript**: For JS we use the [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript).

- **HTML/CSS**: For HTML/CSS we agreed upon the [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.html).

- **XQuery**: We use the [xqdoc style guide](http://xqdoc.org/xquery-style.pdf) with the following addenda:

    - use double quotes instead of single quotes (for easy escaping)
    - use four spaces for a TAB (because eXide switching the preferences in eXide's setting isn't permanent)

- **XSLT**: Since there is no official style guide for XSLT, we decided to write
[our own](https://github.com/subugoe/rdd-technical-reference/tree/master/style-guides/rdd-xslt.md), resulting from common best practices and own experiences within
the department.

- **Python**: For Python [PEP 8](https://www.python.org/dev/peps/pep-0008/) should be used, Django has a style guide based on PEP-8 with some exceptions: [Django-Styleguide](https://docs.djangoproject.com/en/dev/internals/contributing/writing-code/coding-style/). There are linters and tools like [flake-8](https://pypi.org/project/flake8/) and [pep-8](https://pypi.org/project/pep8/) available as support.

- **SPARQL**: For SPARQL there is not really any official style guide and there is no possibility to simply include any code style automatically using a code style file. We just collect some advice how to format and use SPARQL code [here](https://github.com/subugoe/rdd-technical-reference/tree/master/style-guides/rdd-sparql.md).


# Documentation

## Doc Sprints

To ensure the best documentation of our code we meet on a weekly base for a code sprint to document everything we have coded throughout the week and haven't been able to document properly yet. The meeting takes place in the meeting room at 1pm. Cookies may be provided.

## General

- Don't document a language's specifics, e.g. operators.\
*Example:* Use of `=>` in the XQuery expression `replace("qbc", "q", "b") => substring(1, 2)` MUST NOT be explained in a comment.
- It is best to use a language's structure to document.
- Write the best documentation you can.
- Documentation and variable language is American English.
- Docs should be as close to the code as possible.\
This refers both to the documentation in a repository and in the code itself, e.g. inline documentation.
- Every code repository MUST have:

    - a README.md file according to [this template](https://gist.github.com/PurpleBooth/109311bb0361f32d87a2) that contains
        - link to original repository (if the software is forked or otherwise based on preexisting software)
        - short introduction on what the repository is about
        - a guide how to get the software running (if makes sense)
        - link to demo instance
        - example or demo installation
        - link to license file
        - contribution guide
        - link to style guide
        - link to bug tracker/project management system
        - known issues
        - badges to CI status
    - a LICENSE file

## Developer Documentation

### Architecture of the Software

Each software project should be documented using an architecture diagram that helps understanding its basic functionality (even though using tools to generate diagrams such as UML class diagrams doesn't seem to be possible in every case).\

*Examples:*

- [Generating call graphs in eXist-db](https://gitlab.gwdg.de/SADE/SADE/tree/develop/modules/callgraph)

Call diagrams can be useful to follow code and service calls and should be existing for every API method.

### API Documentation

- The docs should comprise used parameters, author and @since annotations

- [Example for Java](https://lab.sub.uni-goettingen.de/self-updating-docs.html)

- Links to callers must not be listed in the documentation, because this info will be deprecated soon. It is strongly recommended to use call stacks of tools like Eclipse (Java) and/or Call Graph Module (SADE).

- Document REST-APIs using [openAPI](https://github.com/OAI/OpenAPI-Specification) if possible. OpenAPI docs should be located at `/doc/api` on servers.

## Admin Documentation

- The docs should comprise how to install the software, how to run and/or restart it, how to test the installation, ...

## Server documentation:

This type of documentation is provided and maintained in our DARIAH wiki space.\

We have a template encompassing all information necessary: To create a wiki page for a new server navigate to the FE Server list, select "..." right beside the "Create" button and search for "FE-Server".

## User Documentation

- how to use the software and APIs, FAQs, walkthroughs, ...

- guided tour (Bootstrap Tour) as user documentation

    - for SADE portal usage (such as Fontane, BdN, Architrave)
    - for complex Digital Editions

- screencasts

### CESSDA's Software Maturity Levels in RDD

#### MUST
`MUST` be SML2, which is defined as follows:

> Use is feasible: There is external documentation that is accessible and sufficient for an expert user to configure and use the software for the user’s individual needs. Terminology and methodology is not explained.

##### Actions to be taken in RDD
- a README(.md) has to be available in the source code repository (already defined in rdd-technical-reference, cf. @@TODO@@)

#### SHOULD

`SHOULD` be SML3, which is defined as follows:

>Use is possible by most users: There is a user manual that can guide a reasonably skilled user through use and customisation of the software to the user’s individual requirements. Documentation is consistent with current version of the software.

##### Actions to be taken in RDD
- a more detailed explanation is available for the user at some place (such as user guide in wikis, etc. p.p)
- docs should also be provided in a docs directory in the source code repository
- docs are revised regularly during our doc sprints



# Which version control do you use? You do use version control, do you?

We exclusively use git in RDD. Please see <https://git-scm.com/doc> for information on how it works.

We recommend to use the [Git flow Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) (also consult the [Cheat Sheet](https://danielkummer.github.io/git-flow-cheatsheet)).
For git flow it is safest to protect your master and develop branch on server side to avoid accidental pushes into these branches. All specific branches working on an issue described in a bug tracker may utilize the following naming scheme:\
\
`[track]/#[ISSUENUMBER]-[KEYWORD]`\
\
e.g. `bugfix/#12-flux-capacitor`.

A GitHub workflow used in DARIAH-DE and related services is described in the [DARIAH-DE Wiki](https://wiki.de.dariah.eu/display/DARIAH3/DARIAH-DE+Release+Management#DARIAH-DEReleaseManagement-Beispielmitdevelop-undmaster-Branch(Gitflow)).

You could also use the [GitLab flow](https://docs.gitlab.com/ee/topics/gitlab_flow.html) as a simpler alternative, which can be broken down into [11 Rules](https://about.gitlab.com/blog/2016/07/27/the-11-rules-of-gitlab-flow/).

It is also recommended to automatically close issues via commit message; How this works exactly depends on the Git repository server. Issues can also be [referenced across repositories](https://help.github.com/articles/autolinked-references-and-urls/#commit-shas).

We use the following Git servers at the moment in RDD:

- Projects (GWDG) --> <https://projects.gwdg.de>
- GitLab (GWDG) --> <https://gitlab.gwdg.de>
- github.org --> <https://github.com/subugoe>


Which one is suitable for you depends on:

- the project you are working on
- existing code
- whether or not you want to use CI/CD or GitLab Runners
- ...



We have got an [RDD team on GitHub](https://github.com/orgs/subugoe/teams/fe). Feel free to join us!


Consider mirroring of repos for project visibility (e.g. mirror GitLab/Projects code to Github?)


# Do you track your bugs properly?

A bug tracking system is obligatory! Please use the respective bug tracking system of your repo and/or project management solution (please see chapter version control)!


# Do you test your software?

We aim to have a test coverage of **100%** (except for getter and setter methods). This is understood on a component level, which means that every method should have at least one test. Whether you achieve this by Test Driven Development (TDD) or not is specific to your preferred way to work.

Please keep in mind not only to write a test for each of your functions but also
to consider all possible outcomes. It is e.g. not sufficient to test if a function
creates a file if the written content depends on variables etc.

Examples for writing tests in different programming languages are:

- [**XQuery**](https://gist.github.com/joewiz/fa32be80749a69fcb8da)


# Building Code and Continuous Integration

## Building Code

Ideally, we use build tools to conveniently get a software running.
The reason for using a build tool is to be able to build and/or test a code project with one command (after checking out). Another reason is to include dependency management.

#### Build tools we are using at the moment

* **bash scripting**: (BdNPrint, FontanePrint)
* **eXist**: Ant (SADE)
* **Java**:
    - Maven (TextGrid)
    - gradle (TextGrid)
* **JavaScript**:
    - bower (DARIAH-DE GeoBrowser, tgForms)
    - cake (tgForms)
    - NPM (DARIAH-DE Publikator, tgForms)
    - rake (DARIAH-DE GeoBrowser)

* **Python**:
    - make (Sphinx documentation)
    - PIP (DiscussData)
* **Ruby**: bundler (DARIAH status page)

#### Build tools we want to evaluate

* gradle

## Continuous Integration

We want to use CI as soon as possible in new projects. Please set up your gitlab-project to show your pipeline-status and test-coverage for your default-branch under Settings/General->Badges. The generic links for all projects are:
* Pipeline-status
    - Link: `https://gitlab.gwdg.de/%{project_path}/commits/%{default_branch}`
    - Badge image URL: `https://gitlab.gwdg.de/%{project_path}/badges/%{default_branch}/pipeline.svg?style=flat-square`
* Test-coverage
    - Link: `https://gitlab.gwdg.de/%{project_path}/commits/%{default_branch}`
    - Badge image URL: `https://gitlab.gwdg.de/%{project_path}/badges/%{default_branch}/coverage.svg?style=flat-square`

The workflows we are using currently in Jenkins and GitLab Runner are:

* Code building
* Testing
* Code analyzer (Sonar)
* Packaging (JAR, WAR, DEB, XAR)
* Distribution (Nexus, APTLY repo, eXist repo)
* Release Management (via GitLab Environments and gitflow)

### Sample configuration of the GitLab Runner

There is a [full and documented example](https://gitlab.gwdg.de/SADE/SADE/blob/develop/.gitlab-ci.yml) of how the GitLab Runner is used in SADE.


### Sample configuration of the Jenkins CI (Multibranch Pipelines)

- On commit and push to the <https://projects.gwdg.de> gitolite repo (such as <https://projects.gwdg.de/projects/tg-crud/repository>) Jenkins on [ci.de.dariah.eu](https://ci.de.dariah.eu/jenkins) is notified (see projects' gitolite configuration)

- Jenkins then does a checkout and build of configured branches (see Jenkins' project's multibranch pipeline configuration such as <https://ci.de.dariah.eu/jenkins/job/DARIAH-DE-CRUD-Services>.

- Stage *Preparation*: Prepare things

- Stage *Build*: Build, JAR, WAR, and DEB packages from source code, deploy JAR and WAR packages to the [Nexus repo](https://nexus.gwdg.de). For further information on Nexus cf. [ci's server documentation](https://wiki.de.dariah.eu/display/FEAD/ci.de.dariah.eu). Jenkins is configured to deploy JARs and WARs via Maven and a Nexus deploy-account.

- Stage *Publish*: Publish DEB packages to the [DARIAH-DE Aptly Repo](https://ci.de.dariah.eu/aptly). Jenkins is using a shared library of scripts and publishing is devided into four conditionals: TG version, DH version, SNAPSHOT version, or RELEASE version due to given version suffixes!


# Deployment and maintenance

## Puppet

For server configuration and setup we use puppet for most servers. The main puppet code is provided in GitLab <https://gitlab.gwdg.de/dariah-de-puppet>. The DARIAH-DE and TextGrid Repository module (dhrep) is contained in Github <https://github.com/DARIAH-DE/puppetmodule-dhrep>.

### Monitoring

- Icinga probes for DARIAH-DE services <https://icinga.de.dariah.eu/icinga>

- Metrics for Sever specific monitoring <https://metrics.gwdg.de>

### Release Management

# Code quality level for RDD

## Code review
We want to ensure code review for all major commits, in gitflow for everything
that is subject to be merged into `develop`.

For projects with more than one developer in the team it is preferred to have code
reviews within the team, in other cases your friendly RDD developer team is
on your side.

- idea: invite all developers to a MR, at least 2 approvals needed for MR taking place. this way, everybody gets the chance to have a look at other people's code

### Sample workflow: Code reviews in SADE

1. A developer decides to work on a feature. She commits her changes to a separate feature branch. After some time she finishes the feature and wants it to be part of the development branch.
2. The developer creates a merge request and assigns everybody she sees fit to properly review her code to it.
3. To avoid diffusion of responsibility, she also assigns one of the chosen assignees as MUST. This means that this person has to approve the MR, otherwise the merge cannot be done. Although GitLab sends notifications to everybody who is newly assigned to a MR, she should notify the MUST assignee personally (in case he or she doesn't notice the mail sent by GitLab).
4. The MUST assignee reviews the changes according to style, variable naming, understandability, documentation provided, functionality, etc. If everything is to his or her liking, he or she approves the MR. The other assignees are free to review the code as well. **Note:** MRs without docs should not be accepted.
5. After the MR has been (dis)approved, the assignee removes his- or herself from the list of assignees. The MUST assignee informs the developer over the review being done.
6. The developer merges her changes into the development branch.



## Proof of concept
When preparing a proof of concept that is always labeled `poc`, a code review is
not necessary.


# Licensing

- clarify software license before programming

- add license to code header

Best practice is to maintain a file listing all third-party packages that are
part of the software. This list should hold the following metadata and SHOULD be
prepared like the table below, always in alphanumeric order.

```
| name | license | origin             |
|------|---------|--------------------|
| foo  | barware | github.com/foo/bar |
```

Maybe the `license-maven` plugin will help you.

# Retirement of software

- clarify if software is no longer supported


# Helpful links and references

- EURISE-network technical-reference:\
<https://github.com/eurise-network/technical-reference>

- DHTech -- An international grass-roots community of Digital Humanities software engineers:\
<https://dh-tech.github.io>

- The Software Sustainability Institute, Guidelines and Publications:\
<https://www.software.ac.uk>

- The Joel Test: 12 Steps to Better Code:\
<https://www.joelonsoftware.com/2000/08/09/the-joel-test-12-steps-to-better-code>

- Software Quality Guidelines:\
<https://github.com/CLARIAH/software-quality-guidelines>

- Software Testing Levels:\
<http://softwaretestingfundamentals.com/software-testing-levels>

- Netherlands eScience Center Guide\
<https://guide.esciencecenter.nl>
