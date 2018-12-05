---
layout: post
title: "Advent of Code Day 2"
tags:
  - code
modified: 2018-12-02
---

Day 2 of Advent of Code[^1]. 

The following is my solution for Part 2.
Part 1 was some modification of this.

{% highlight python %}
import collections
 
lines = []
for line in open("input2.txt"):
    lines.append(line.strip())
 
# lines.sort() // unsure if saves time or wastes time
 
for i in range(len(lines)):
    for j in range(i,len(lines)):
        x = [ord(a) ^ ord(b) for a,b in zip(lines[i],lines[j])]
        xc = sum(i > 0 for i in x)
        if xc == 1:
            print(lines[i])
            print(lines[j])
            exit()
{% endhighlight %}


As I had labeled in the comment, sorting the lines didn't appear to cause a noticeable difference in performance for the input size. I haven't looked at the effects on larger or smaller inputs, but from what I gathered from a friend that running similar code in Clojure, sorting did have a magnitude of performance increase.


[^1]: [https://adventofcode.com/2018/day/2](https://adventofcode.com/2018/day/2)
