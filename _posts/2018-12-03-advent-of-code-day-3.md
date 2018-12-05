---
layout: post
title: "Advent of Code Day 3"
tags:
  - code
modified: 2018-12-03
---

Day 3 of Advent of Code[^1]. 

This is kind of a mess. I was really rushing to try to see if I could land on the leaderboard at least once this year.

{% highlight python %}
import re

pattern = re.compile(
        """
        \#
        (?P<claim>.*?)
        \s@\s
        (?P<left>.*?)
        ,
        (?P<top>.*?)
        :\s
        (?P<x>.*?)
        [x]
        (?P<y>.*?)
        $
        """, re.VERBOSE)

matches = []
for line in open("input3.txt"):
    match = pattern.match(line)
    claim = int(match.group('claim'))
    top = int(match.group('top'))
    left = int(match.group('left'))
    x = int(match.group('x'))
    y = int(match.group('y'))
    matches.append({"top": top, "left": left, "x": x, "y": y})

c = set()
collide = set()
for match in matches:
    for i in range(match['left'],match['left']+match['x']):
        for j in range(match['top'],match['top']+match['y']):
            if (i,j) in c:
                collide.add((i,j))
            c.add((i,j))

print(len(collide))

for match in matches:
    found = True
    for i in range(match['left'],match['left']+match['x']):
        for j in range(match['top'],match['top']+match['y']):
            if (i,j) in collide:
                found = False
    
    if found:
        print(claim)
{% endhighlight %}


[^1]: [https://adventofcode.com/2018/day/3](https://adventofcode.com/2018/day/3)
