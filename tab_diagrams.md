---
title: Diagrams
layout: null
tags: threat-modeling threat modeling dataflow-diagram dataflow diagram python graphviz plantuml
tab: true
order: 4
---

Diagrams are output as [Dot](https://graphviz.gitlab.io/) and [PlantUML](https://plantuml.com/).

When `--dfd` argument is passed to the above `tm.py` file it generates output to stdout, which is fed to Graphviz's dot to generate the Data Flow Diagram:

```bash

tm.py --dfd | dot -Tpng -o sample.png

```

Generates this diagram:

![dfd.png](/assets/images/dfd.png)


The following command generates a Sequence diagram.

```bash

tm.py --seq | java -Djava.awt.headless=true -jar plantuml.jar -tpng -pipe > seq.png

```

Generates this diagram:

![seq.png](/assets/images/seq.png)
