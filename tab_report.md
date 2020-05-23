The diagrams and findings can be included in the template to create a final report:

```bash

tm.py --report docs/template.md | pandoc -f markdown -t html > report.html

```
The templating format used in the report template is very simple:

```text

# Threat Model Sample
***

## System Description

{tm.description}

## Dataflow Diagram

![Level 0 DFD](dfd.png)

## Dataflows

Name|From|To |Data|Protocol|Port
----|----|---|----|--------|----
{dataflows:repeat:{{item.name}}|{{item.source.name}}|{{item.sink.name}}|{{item.data}}|{{item.protocol}}|{{item.dstPort}}
}

## Findings

{findings:repeat:* {{item.description}} on element "{{item.target}}"
}

```

To group findings by elements, use a more advanced, nested loop:

```text
## Findings

{elements:repeat:{{item.findings:if:
### {{item.name}}

{{item.findings:repeat:
**Threat**: {{{{item.id}}}} - {{{{item.description}}}}

**Severity**: {{{{item.severity}}}}

**Mitigations**: {{{{item.mitigations}}}}

**References**: {{{{item.references}}}}

}}}}}
```

All items inside a loop must be escaped, doubling the braces, so `{item.name}` becomes `{{item.name}}`.
The example above uses two nested loops, so items in the inner loop must be escaped twice, that's why they're using four braces.
