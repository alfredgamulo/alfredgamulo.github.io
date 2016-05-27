---
layout: post
title: "Bash test operators"
description: "Example Bash operators"
tags: 
  - code
modified: 2013-10-09
---

Consider yourself a bash pro? I bet you don’t even know the third thing about bash scripting. That’s right, its about test operators and you’re about to get schooled. Here’s my cheat sheet. Feel free to print it out and put it on your cube. Beware, your friends will think you’re a total noob.

| Math Operators | Meaning |
|:---------------|:--------|
| -eq | equal to |
| -ne | not equal to |
| -lt | less than |
| -le | less than or equal to |
| -gt | greater than |
| -ge | greater than or equal to |
| **String Operators** |
|:---------------------|
| =	 | equal to |
| != | 	not equal to |
| -n | 	not null and exists |
| -z | 	null and exists |
| **File Operators** |
|:------------------ |
| -s | 	not empty |
| -f | 	is file and not a directory |
| -d | 	is directory and not a file |
| -w | 	is writeable |
| -r | 	is read-only |
| -x | 	is executable |
| **Logical Operators** |
|:------------------ |
| !	 | not |
| -a | 	and |
| -o | 	or |
{: rules="groups"}