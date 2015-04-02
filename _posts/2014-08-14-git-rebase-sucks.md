---
layout: post
title: "Git rebase sucks"
description: "Workaround if rebasing is causing problems"
tags: [code]
modified: 2014-08-14
---

Git was being a real pain in the ass today. I’m not the biggest fan of git rebasing, but I understand that some teams prefer to use it to keep the code history clean.
Today’s problem arose from canceling a pull request, then requiring new changes to be made on my feature branch while the master branch had ongoing development. By the time I had made my new changes and tried to rebase with master, I was experiencing a butt load of merge conflicts that I just didn’t want to deal with.

So the steps that lead to my problem was as follows:

1. create feature branch
2. write code in feature branch
3. rebase with master
4. commit and push feature branch
5. create pull request
6. decline pull request
7. write code in feature branch
8. team member simultaneously updated master
9. rebase with master

I was trying to rebase with master because my team practices rebasing with master before performing pull requests. However, that last rebase really screwed things up for me as far as merge conflicts go.
My solution to preventing all of that headache is as follows. Rather than performing a vanilla rebase with master that second time, perform `git rebase --onto master`. This changes the starting point at which to create new commits. Basically it changes your feature branch to look just like master. At this point if you perform `git status` you will see that your local branch and the remote branch have diverged commits. Now you can simply perform `git pull` to play the remote branch commits on top of your local branch. Now perform any necessary code changes as required before then commit and push. Last step is to drink a beer because PHEW that was hard work!

To summarize, if you think you need to rebase your feature branch with master, but you feel like you may run into a merge headache try: `git rebase --onto master && git pull`

:)