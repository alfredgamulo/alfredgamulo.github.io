---
layout: post
title: "Advent of Code Day 4"
tags:
  - code
modified: 2018-12-04
---

Day 4 of Advent of Code[^1]. 

I really like Python for these types of coding challenges. The data size is such that performance is negligible. It's really easy to lay out your thoughts and reread the code without troubling yourself with complex syntax written for performance's sake.

In this challenge, I use regex matching again to capture the minutes and IDs of the guards. Then I loop twice for each part of the challenge. I could have combined them into one or two loops, but again performance isn't a priority over readability while attacking the puzzle.

{% highlight python %}
import re

lines = []
for line in open("input4.txt"):
    lines.append(line.strip())
lines.sort()

pattern = re.compile('\[\d{4}-\d{2}-\d{2}\s(?P<hour>\d{2}?):(?P<minute>\d{2}?)\]\s(?P<msg>.*?)$')
id = None
sleeps = {}
for line in lines:
    s = pattern.match(line)
    msg = str(s.group('msg'))
    if 'Guard' in msg:
        id = str(msg.split(' ')[1].split('#')[1])
    if 'falls' in msg:
        start = int(s.group('minute'))
    if 'wakes' in msg:
        end = int(s.group('minute'))
        if id not in sleeps:
            sleeps[id] = []
        sleeps[id].extend(list(range(start,end)))

# part 1
g_longest = 0
g_id = None
g_minute = 0
for g,v in sleeps.items():
    if len(v) > g_longest:
        g_longest = len(v)
        g_id = g
        g_minute = max(set(v), key=v.count)

print(int(g_id)*int(g_minute))

# part 2
g_id = None
g_minute = 0
g_count = 0
for g,v in sleeps.items():
    minute = max(set(v), key=v.count)
    count = v.count(minute)
    if count > g_count:
        g_count = count
        g_id = g
        g_minute = minute

print(int(g_id)*int(g_minute))
{% endhighlight %}


[^1]: [https://adventofcode.com/2018](https://adventofcode.com/2018)