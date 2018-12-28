---
layout: post
title: "Google Spreadsheets as JSON"
tags:
  - code
modified: 2018-12-27
---

For some use cases it is very easy to use a Google Sheet as the datasource for a website. For example, I've used a published Google spreadsheet as the backend data store for a competition leaderboard. This proves to be one of the simplest solutions as several moderators may want quick access to update the leaderboard and it can be updated easily from a mobile device.


It's quite simple to publish the data from a Google Sheet as JSON:

1. Click the blue share button on the top right of the Sheet console to get a shareable link. For this step, have it set so that "Anyone with the link **can view**". What this does is two things: it publishes the sheet to be made available publicly, and it also gives you the necessary `SHEET ID` for the following steps. Example:
    > ```https://docs.google.com/spreadsheets/d/<SHEET_ID>/edit?usp=sharing```

2. Insert the `SHEET ID` that you got from the Step 1 and insert it into the URL template:
    > ```https://spreadsheets.google.com/feeds/list/<SHEET_ID>/od6/public/values?alt=json```