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


### CESSDA's Software Maturity Levels in RDD (CA1.3)

#### MUST

`MUST` be SML2, which is defined as follows:

> There is external documentation that describes public API functionality and is sufficient to be used by an experienced developer. If available, source code is consistently and clearly commented. Source code naming conventions are adhered to and consistent.

#### Actions to be taken in RDD
- public API is fully documented, e.g. by using OpenAPI
- naming conventions still have to be discussed --> style guide?
- reference to style guide used in the CONTRIBUTING/README file?


## Admin Documentation

- The docs should comprise how to install the software, how to run and/or restart it, how to test the installation, ...

### CESSDA's Software Maturity Levels in RDD (CA1.2)

#### MUST

`MUST` be SML3, which is defined as follows:

> There is a deployment and configuration manual that can guide an experienced operational user through deployment, management and configuration of the software. Exception and failure messages are explained, but descriptions of solutions are not available. Documentation is consistent with current version of the software.

#### Actions to be taken in RDD
- deployment: short deployment descriptions can be provided in the README, more detailed explanations should be kept separately (such as INSTALL(.md), linked there from README)
- exception and failure messages are described in doc strings/function annotations
- function documentation should be generated automatically and made available/searchable in the web (such as readthedocs, javadoc html, etc. pp.)



## Server Documentation

This type of documentation is provided and maintained in our DARIAH wiki space.\

We have a template encompassing all information necessary: To create a wiki page for a new server navigate to the FE Server list, select "..." right beside the "Create" button and search for "FE-Server".


## User Documentation

- how to use the software and APIs, FAQs, walkthroughs, ...

- guided tour (Bootstrap Tour) as user documentation

    - for SADE portal usage (such as Fontane, BdN, Architrave)
    - for complex Digital Editions

- screencasts

### CESSDA's Software Maturity Levels in RDD (CA1.1)

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



# Version control

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


# Bug Tracking

A bug tracking system is obligatory! Please use the respective bug tracking system of your repo and/or project management solution (please see chapter version control)!


# Software Tests

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

* **bash scripting**: (bdnPrint, FontanePrint)
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


## Packaging

### CESSDA's Software Maturity Levels in RDD (CA5)

##### MUST

`MUST` be SML5, which is defined as follows:

> Demonstrable usability: A Continuous Integration server job (or equivalent) is available to deploy the packaged/containerised software. Administrators are notified if deployment fails. Versions of deployed software can be upgraded/rolled back from a Continuous Integration server job (or equivalent). Data and/or index files can be restored from a Continuous Integration server job (or equivalent).

##### Actions to be taken in RDD
- examples for versions of deployed software: versioning of deb packages
- examples for rollback: rebuild index ElasticSearch from source data, restore database backup



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


# Intellectual Property

## Licensing

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

## CESSDA's Software Maturity Levels in RDD (CA2)

##### MUST

`MUST` be SML5, which is defined as follows:

> Demonstrable usability: There are multiple statements embedded into the software product describing unrestricted rights and any conditions for use, including commercial and non-commercial use, and the recommended citation. The list of developers is embedded in the source code of the product, in the documentation, and in the expression of the software upon execution. The intellectual property rights statements are expressed in legal language, machine-readable code, and in concise statements in language that can be understood by laypersons, such as a pre-written, recognisable license.

##### Actions to be taken in RDD
- see rdd-technical-reference for choosing the license
    - source code: use OSI approved licenses? (see https://opensource.org/licenses) (++TODO discuss in fe-develop++) (how to chose a license?: http://freesoftwaremagazine.com/articles/choosing_and_using_free_licenses_software_hardware_and_aesthetic_works/fig_choosing_license.jpg)
        - assets: CC0? CC-BY-SA? (++TODO discuss in fe-develop++)
- we reach SML5 by providing a license file on root level containing the license text (GPL wants its license text in a file called COPYING [see https://www.gnu.org/licenses/gpl-howto.de.html] other licenses use LICENSE)
- if the license text is not contained in the license file, we provide the full license text in another file  (++TODO++) (https://softdev4research.github.io/4OSS-lesson/03-use-license/index.html#add-a-licence-file-to-a-repository)
- in the source code header the license statement is added to every file. GPL example:

```
    This file is part of FOOBAR.

    FOOBAR is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    FOOBAR is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with FOOBAR.  If not, see <https://www.gnu.org/licenses/>.
```

- the names of all contributed developers are stored in a contributors file on root level (every user that has committed in the repository)
- in the source code the contributors are added to each class/method/function/file/etcpp
- “and in the expression of the software upon execution“ -- if applicable

# CESSDA – Decisions

## CA3: Extensibility

MUST be __SML3__:

„Use is possible by most users: Future extensibility is designed into the system for a moderate range of use cases. The procedures for extending the software are defined, whether by source code modification or through the provision of some type of extension functionality (e.g., callback hooks or scripting capabilities). Where source code modification is part of the extension plan, the software is well-structured, has a moderate to high level of cohesion, and has configuration elements clearly separated from logic and display elements.“

__Actions to be taken in RDD:__
- Future extensibility is designed into the system
    - on RDD developer level
    - source code modification --> software is well-structured
    - provision of some type of extension functionality --> use of frameworks such as templating engines and localization frameworks
    - configuration elements clearly separated from logic and display elements
- use SADE as example project


## CA4: Modularity

MUST be __SML3__:

„Use is possible by most users: There is evidence that the architecture is open, with full structuring into individual components that provide functions or services to outside entities (i.e., open architecture); internal functions or services documented, but not consistently; modules have been created for generic functions, but modules have not been created for all of the specified functions; code within each module contains many independent logical paths.“

SHOULD be __SML5__:

„Demonstrable usability: It is evident that all functions and data are encapsulated into objects or accessible through web service interfaces. There is consistent error handling with meaningful messages and advice, and use of generic extensions to program languages for stronger type checking and compilation-time error checking. Services are available externally and code within each module contains few independent logical paths.“

__Actions to be taken in RDD:__
- we NEED consistent error handling with meaningful messages and advice
- if specific errors can occur --> create explicit errors
- return and input types must be defined if language allows types
- think of possible reuse of internal methods --> make them externally available
- one module serves one purpose


## CA6: Portability

(target platform: e.g. Docker container)

MUST BE __SML5__:

„Demonstrable usability: The software is completely portable to the target platform. In theory at least, the software will run on the target platform provided it is packaged/containerised.“

__Actions to be taken in RDD:__
- examples for target platforms: TextGridLab (Windows, Linux, Mac OS), Java Web Services (Web Application Server: Tomcat, etcpp), SADE (eXistDB, Linux, Windows), DiscussData-Django-App (jeder Host, für den Docker verfügbar ist)

    ++ Michelle möchte, dass wir mehr über Docker sprechen! ++


## CA7: Standards Compliance

MUST BE __SML3__:

„Use is possible by most users: The software and software development process comply with open, recognised or proprietary standards, but there is incomplete verification of compliance. Compliance to recognised standards has be tested but this may not be for all components. There is documented evidence of standards being used, but not of the verification of components.“

__Actions to be taken in RDD:__
- coding standards: code style, git (commit hooks), gitflow/gitlabflow, (semantic) versioning
- software standards: documentation (JavaDoc, OpenAPI, etcpp), data and metadata formats, APIs (REST, SOAP, OAI-PMH, etcpp), license
- CI standards: release workflow (?), deployment


## CA8: Support

MUST BE __SML1__:
__Actions to be taken in RDD:__
- an organizational e-mail-adress must be provided with the readme and in a convenient view, e.g. imprint/help/info etc.

SHOULD BE __SML3__:
__Actions to be taken in RDD:__
- provide support "near" the source code (discussable)
- by any means, provide it in *one* location
- regular and planned releases


## CA9: Verification and Testing

__Actions to be taken in RDD:__
- CESSDAs definitions seems a bit unclear to us
- without referencing the SMLs we link our test chapter to CESSDAs document


## CA10: Security

MUST BE __SML2__:

__Actions to be taken in RDD:__
- every developer must have had a basic security training

SHOULD BE __SML5__:

__Actions to be taken in RDD:__
- address security in every step of development (design, implementation, testing and verification, release)

__TODO__:
- mit AL über Training für alle Developer sprechen
- Anforderungen an Softwaresicherheit formulieren
- Training erarbeiten (mit Security-Issue-Liste beginnen)


## CA11: Internationalisation and Localisation

MUST BE __SML1,5__

__Actions to be taken in RDD:__
- locale awareness is a high requirement for software with a monolingual target audience but you must provide it in english (and/or the target language) at least

SHOULD BE __SML3__

__Actions to be taken in RDD:__
- if applicable, i18n and l10n frameworks should be used

nice to read: https://bridge360blog.com/2011/11/25/software-design-considerations-for-internationalization-and-localization/


## CA12: Authentication and Authorisation

MUST BE __SML2__
SHOULD BE __SML4__

In this case we cannot give a general recommendation since the way authentication and authorisation is implemented inherently depends on the software's functionality. Instead of developing an own solution rely on DARIAH's AAI whenever possible.

__Actions to be taken in RDD:__
- never share passwords
- use Shibboleth whenever possible and reasonable



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
