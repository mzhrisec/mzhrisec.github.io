---
layout: post
title:  "How to Narrow Recon giving me $$$$ Bounty"
date:   2023-04-17 22:07:00 +0000
author: Mohammad Zaheri
tags:   [Writeups,Web]
description: "Just another writeup about web applications and recon"  
---

## Introduction

In this writeup, I explain how to get 4 digit bounty with web applications recon and I hope this article will be helpful for you.

## Program Scope and technologies 
In the past month in invited to a private program in Hacker0ne, i usually work on a program with limited scope, and this program just has a sandbox domain: (sandbox.target.tld) and they started the bounty program in Q1 of 2022, I pick up the domain and open my BurpSuite 

## Recon 
I signed up using my alias email. after quickly browsing the web application i saw my BurpSuite history, all requests are GraphQL POST method request. I understood finding Bug in this program is hard but i never give up :D


![POST requests](/imgs/inline/fupost.png)

### Patience and discipline is a key

after clicking every item on the site and working with it, i understand how the application works. 
The interesting part was that the application sending a GET request to ```GET /api/auth/csrf``` endpoint for geting new csrf token.
this endpoint vulnerable to [Web Cache Deception Attack](https://omergil.blogspot.com/2017/02/web-cache-deception-attack.html), but in not really impactful

![WCDA on CSRF endpoint](/imgs/inline/csrfe.png)

I decided to find an endpoint that would return sensitive information and started fuzzing the ```GET /api/auth/FUZZ``` endpoint 
after some time i found interesting endpoint which returns sensitive information and vulnerable to Web Cache Deception Attack :D

with this endpoint i can access the all user information and api keys 

![:D](/imgs/inline/donecd.png)

I reported that to the program and they triaged it as critical 

Thanks for reading if you have any questions please reach me out 

