---
title: >-
  Github Message 'Support for password authentication was removed. Please use a
  personal access token instead.' FIX
date: 2022-10-28 01:22:44
tags:
---

#### 1. Create Personal Access Token on GitHub

From your GitHub account, go to Settings => Developer Settings => Personal Access Token => Generate New Token (Give your password) => Fillup the form => click Generate token => Copy the generated Token, it will be something like ghp_dah6caPui1ov2vei2quai2phaeZiekeing5h


#### 2. configure your local github repo for POT

```
$ git config --global user.name "your-GITHUB-USERNAME"
$ git config --global user.email "YOUR-GITHUB-EMAIL"
$ git config -l
```


