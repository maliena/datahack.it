---
layout: post
title:  CSV to JSON Conversion in Python
date:   2013-06-13 17:02:16
categories: Python
description: How to convert a CSV-file into JSON? This Python code snippet helps you to generate a proper and valid JSON-file!
---

When it comes to data like a list of [top level domains](https://gist.github.com/jbspeakr/4466385) (TLDs) or similar small and mostly flat datasets, I prefer to work with JSON as a fundamental data structure. The reason for that is not just its great human-readability (which is really nice to have for newcomers), but also the smooth interaction with e.g. Python and JavaScript.

Nevertheless it seems that the majority of open datasets is still published as classic CSV-files. This is totally fine regarding its highly compressed way of storing information, but sometimes you just want to have something much clearer.

For that reason, you would probably want to convert your CSV-file into a proper and valid JSON-file. The following Python-Script is doing exactly this conversation:

### Python-Script: Convert CSV to JSON
{% highlight python %}
import csv
import json

i = open('input.csv', 'r')
reader = csv.DictReader(i)
data = json.dumps([row for row in reader], indent=4)

o = open('output.json', 'w')
o.write(data)
{% endhighlight %}

In my eyes, the script is greatly self-explaining, what makes it unnecessary to bloat it with redundant comments. If you have any question, write a comment and I'll get back to you asap!

*[JSON]: JavaScript Object Notation
*[CSV]: Comma-Separated Values
