# The SUB RDD SparQL Style Guide

## Purpose

This document serves to establish consistent SparQL code style for all projects (from June 2018 on) in the SUB Research and Development Department.

The structure of this document is inspired by [Google's HTML and CSS style](https://google.github.io/styleguide/htmlcssguide.html) guide.

## General Style Rules

- declaration of variables should start with a **?** (and not with a **$**).
- opening parenthesis **{** should be at the end of the line. Closing parenthesis in a separate line. Example:

```
SELECT * WHERE {
?s ?p ?o .
} LIMIT 10
```

'''
- group concatenations in SELECT command should be in seperate lines.
'''

```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX dct: <http://purl.org/dc/terms/>

SELECT DISTINCT
(group_concat( distinct ?conceptName;separator="; ") as ?conceptNames)
(group_concat( distinct ?conceptUri;separator="; ") as ?conceptUris)
(group_concat( distinct ?next;separator="; ") as ?nexts)
(group_concat( distinct ?def;separator="; ") as ?defs)
WHERE {
<' + uri + '> skos:narrower ?conceptUri.
?conceptUri skos:prefLabel ?conceptName.
OPTIONAL {?conceptUri skos:narrower ?next.}
OPTIONAL {?conceptUri skos:definition ?def.}
FILTER(LANG(?conceptName) = "" || LANGMATCHES(LANG(?conceptName), "en"))
} GROUP BY ?conceptUri
```
