---
layout: post
title: "How to update git commit dates"
date: 2014-04-30
---

1. Start rebase process with 


    ~~~ powershell
    git rebase -i HEAD~<number of commits to rebase>
    ~~~


2. Editor is show. Change all `pick` to `edit` for the ones you want to update. Save and exit editor

3. Then for each commit rebase do the following:
    
    * Set environment variable for GIT_COMMITTER_DATE to the date you want to update to, i.e:


        ~~~
        $env:GIT_COMMITTER_DATE = "2020-05-05T14:00:00 -0600"
        ~~~


    * Next do a commit with the updated dates:


        ~~~ powershell
        git commit --amend --no-edit --date=$env:GIT_COMMITTER_DATE
        ~~~


    * Then continue to the next commit to rebase by typing:


        ~~~
        git rebase --continue
        ~~~


    *Note - These examples are using PowerShell as the command line*
