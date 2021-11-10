---
title: Usage
layout: null
tags: threat-modeling threat modeling dataflow-diagram dataflow diagram python graphviz plantuml
tab: true
order: 2
---

Requirements:

* Linux/MacOS/Windows
* Python 3.x
* Graphviz package
* Java (OpenJDK 10 or 11)
* [plantuml.jar](http://sourceforge.net/projects/plantuml/files/plantuml.jar/download)

```text
tm.py [-h] [--debug] [--dfd] [--report REPORT] [--exclude EXCLUDE] [--seq] [--list] [--describe DESCRIBE]

optional arguments:
  -h, --help           show this help message and exit
  --debug              print debug messages
  --dfd                output DFD (default)
  --report REPORT      output report using the named template file (sample template file is under docs/template.md)
  --exclude EXCLUDE    specify threat IDs to be ignored
  --seq                output sequential diagram
  --list               list all available threats
  --describe DESCRIBE  describe the properties available for a given element

```

Currently available elements are: TM, Element, Server, ExternalEntity, Datastore, Actor, Process, SetOfProcesses, Dataflow, Boundary and Lambda.

The available properties of an element can be listed by using `--describe` followed by the name of an element:

```text

(pytm) ➜  pytm git:(master) ✗ ./tm.py --describe Element
Element class attributes:
  OS
  definesConnectionTimeout        default: False
  description
  handlesResources                default: False
  implementsAuthenticationScheme  default: False
  implementsNonce                 default: False
  inBoundary
  inScope                         Is the element in scope of the threat model, default: True
  isAdmin                         default: False
  isHardened                      default: False
  name                            required
  onAWS                           default: False

```
