---
title: A Note on How to Connect R Studio to GitHub
author: Wes H Cooper
date: '2022-05-14'
slug: []
categories:
  - R
draft: true
tags: [R Studio, GitHub, personal acccess token]
description: A short explanation of how to connect R Studio to GitHub via personal access token.
---

## 1. Sign up at GitHub.com ################################################

If you do not have a GitHub account, sign up here:
https://github.com/join

## 2. Install git ##########################################################

If you do not have git installed, please do so: 
Windows ->  https://git-scm.com/download/win
Mac     ->  https://git-scm.com/download/mac
Linux   ->  https://git-scm.com/download/linux
             or: $ sudo dnf install git-all


## 3. Configure git with Rstudio ############################################

set your user name and email:
`usethis::use_git_config(user.name = "YourName", user.email = "your@mail.com")`

create a personal access token for authentication:
`usethis::create_github_token()` 
in case usethis version < 2.0.0: usethis::browse_github_token() (or even better: update usethis!)

set personal access token:
`credentials::set_github_pat("YourPAT")`

or store it manually in '.Renviron':
`usethis::edit_r_environ()`

store your personal access token with: 
`GITHUB_PAT=xxxyyyzzz`

and make sure '.Renviron' ends with a newline


## 4. Restart R! ###########################################################


## 5. Verify settings ######################################################

`usethis::git_sitrep()`

Your username and email should be stated correctly in the output. 
Also, the report shoud cotain something like:
'Personal access token: '<found in env var>''

If you are still having troubles, read the output carefully.
It might be that the PAT is still not updated in your `.Renviron` file.
Call `usethis::edit_r_environ()` to update that file manually.

## THAT'S IT!