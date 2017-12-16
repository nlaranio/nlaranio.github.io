---
layout: essay
type: essay
title: "Meteor Bugs"
date: 2017-10-19
labels:
  - Software Engineering
  - Meteor
  - Bugs
  
---

### Meteor: Uncaught RangeError: Maximum call stack size exceeded

This is to remedy the Meteor error;

### hasStacks = !!e.stack;

### RangeError: Maximum call stack size exceeded

That pops up on Windows operating system for any Meteor command entered.

1) uninstall NodeJS & Meteor

2) Ensure Node directory under ProgramFiles (x86) is removed and delete all npm directories under {User}/AppData

3) Restart Computer

4) Reinstall Meteor and Node

5) Restart Computer

this should resolve the issue.

This took much trial and error, not to mention hours of installing and looking through forums to dig up this solution. It would seem as though an issue as large as this which prevents Meteor being used at all would have a lot of attention from the people behind meteor but it doesn't appear to be that way. This results in the community to depend on each other for solving issues.

Credit to https://github.com/sproleee who's post solved this for me.

### Meteor Hang up and install

An issue that I ran in to for hours was a hang up upon running Meteor where it would take ridiculously long to unzip files. It turned out to be trying to install a newer version after letting it sit for about an hour which seems strange as downloading the framework and installing it only took 10 minutes at the most for me. While doing some research thinking this was some sort of error and letting it run in the background one thing that came up was the unzipper. Meteor apparently uses 7zip and even comes with its own install version when you download meteor. People were finding that removing its version of 7zip and using the 7zip from the 7zip site tended to speed this process up.
