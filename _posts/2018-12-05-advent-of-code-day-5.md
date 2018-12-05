---
layout: post
title: "Advent of Code Day 5"
tags:
  - code
modified: 2018-12-05
---

Day 5 of Advent of Code[^1]. 

This was relatively easier than yesterday's puzzle.
I wasted some time trying to figure out if I could solve it with a zip and list processing but eventually just went for a brute force approach for the sake of submitting earlier.

{% highlight python %}
def run(polymer):
    done = False
    while not done:
        lngth = len(polymer)
        i = 0
        found = False
        while i < lngth-1:
            j = 1 + i
            if 32 == ( ord(polymer[i]) ^ ord(polymer[j]) ) :
                del polymer[i]
                del polymer[i]
                lngth = lngth - 2
                found = True
            else:
                i = 1 + i
        done = not found
    return polymer

with open("input5.txt") as f:
    polymer = list(f.readline().strip())

part1 = run(polymer)
print(len(part1))

min = 10000 #arbitrary, larger than part 1
# A = 65, Z = 90
for i in range(65,91):
    test_polymer = [a for a in polymer if (ord(a) != i) and (ord(a) != (i+32))]
    test_run = run(test_polymer)
    if min > len(test_run):
        min = len(test_run)

print(min)
{% endhighlight %}


[^1]: [https://adventofcode.com/2018/day/5](https://adventofcode.com/2018/day/5)