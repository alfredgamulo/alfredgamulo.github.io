---
layout: post
title: "Advent of Code Day 1"
tags:
  - code
modified: 2018-12-01
---

I started playing around with Advent of Code[^1] this year. 

For part 1, I used a spreadsheet to sum the numbers :P
Here's my solution for part 2:

{% highlight python %}
found = False
u = set()
i = 0
while not found:
    for line in open("input1.txt"):
        i = i + int(line)
        if i in u:
            found = i
            break
        u.add(i)
        print('.', end='', flush=True)

print(f'found:{found}')
{% endhighlight %}



[^1]: [https://adventofcode.com/2018](https://adventofcode.com/2018)
