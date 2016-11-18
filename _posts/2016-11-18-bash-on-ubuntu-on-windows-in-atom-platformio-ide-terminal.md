---
layout: post
title: "Bash on Ubuntu on Windows in Atom's PlatformIO-IDE-Terminal"
description: "Shortcut to making bash accessible to all of your cmd terminals"
tags:
  - code
modified: 2016-11-18
---

For a while, I've been using specific IDEs for each individual language that I program in. It was feeling cluttered juggling between IntelliJ, Sublime, ZBStudio, et al.

I wanted to give Atom a try to see how it sets itself apart from the rest and to see how I could make it more useful for myself as I switch contexts between all the languages.

One of the great things on Atom is how extensible it is with the package explorer. I loved the feature of having the console in ZBStudio and Sublime. Though Sublime was difficult to configure and ZBStudio was only for Lua. The terminal on Atom's PlatformIO-IDE-Terminal opens a Powershell window when opened. This was good and I really wanted a way to open bash at my project folder's location.

The following details the simple steps to add bash to your Path and be able to use bash at your project folder's location:
<br/>

Make a Link to bash
---
First, make a link to bash.
I created the C:\\Links directory after realizing how powerful these steps are for adding any binary to my PATH

{% highlight ps1 %}
PS C:\Links> mklink bash.exe "C:\Windows\System32\bash.exe
{% endhighlight %}

Second, add this folder to your PATH.

Third, open any terminal whether its Atom's terminal, cmd, or powershell and just type bash.
This will open bash at that location.
This is great because you no longer have to open the Bash application and cd all the way to your project folder.
I never knew until now that `mklink` existed on Windows and will probably use it more to keep my PATH clean by linking everything to my `C:\Links` directory.
<br/>
