---
layout: post
title:  CSV to YAML Conversion in Python
date:   2013-06-25 16:20:00
categories: Python
description: Converting CSV into YAML is an easy task using the following Python code snippet! It helps generating proper and valid YAML-files!
---

YAML Ain't Markup Language, for what reason it is often used for data-oriented, rather than document markup. With its XML-inspired structure, YAML is used widely for setting files and to store large datasets.

If you have plain CSV-files but would like to work using YAML, you need something like a CVS-to-YAML converter. The following Python-Script is doing exactly this conversation and creates valid YAML:

### Python-Script: Convert CSV to YAML
{% highlight python %}
import csv
import yaml

i = open('input.csv', 'r')
reader = csv.DictReader(i)

data = yaml.safe_dump([row for row in reader], canonical=False,
                      encoding='utf-8', allow_unicode=True,
                      default_flow_style=False)

o = open('output.yaml', 'w')
o.write(data)
{% endhighlight %}

In my eyes, the script is greatly self-explaining, what makes it unnecessary to bloat it with redundant comments. Nevertheless, I am going to explain some of the YAML conversion parameters.

- First, the used **safe_dump** method "produces only standard YAML tags" as it is stated in the [PyYAML doc](http://pyyaml.org/wiki/PyYAMLDocumentation#DumpingYAML) and for that reason "can not represent an arbitrary Python object".
- The **encoding** and **allow_uniode** parameters should be pretty straight forward.
- With **canonical** enabled, the dumper explicitly defines the types of the values within the YAML.
- Disabling the **default_flow_style** results in a more human-readable output.

If you have any question, write a comment and I'll get back to you asap!

*[JSON]: JavaScript Object Notation
*[CSV]: Comma-Separated Values
*[YAML]: YAML Ain't Markup Language
*[XML]: Extensible Markup Language
