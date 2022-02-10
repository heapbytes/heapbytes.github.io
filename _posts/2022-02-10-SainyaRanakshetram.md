---
title: "Sainya Ranakshetram CTF"
date: 2022-02-10  21:15:00 +0530 
layout: post
categories: blog
tags: [blog]
pin: true
toc: true
---


# My experience in this CTF

![image](https://user-images.githubusercontent.com/56447720/153431580-0cfe0fac-6ac0-4d35-901a-6713e06c6b19.png)
Official url : https://www.sainya-ranakshetram.in/

## Scoreboard

I ranked `2nd in India` out of 50k+ registrations placed, I've submitted all the flags but the time I took submit them was quite more than the winner

## Short info on this Hackathon

Sainya Ranakshetram had `3 tracks`,
 
1. SECURE CODING 
  > Secure coding was similar to reversing engineering, Reverse engineering is used in software design to enable the programmer or developer to incorporate new features into existing software whether the source code is known or not.

2. CAPTURE THE FLAG
  > Capture the flag (CTF) has challenges of different categories such as cryptography, binary exploitaion, misc, web, etc where the user needs to find vulnerability in that code to exploit it and submit the flag 

3. SDR (Software Defined Radio)
  > Software Defined Radio is the leading edge of information security research. In a modern society with radio signals surrounding us from every direction, SDR can be used to combine the power of our PC and software tools to capture, emulate, decode, replay and otherwise hack these signals!


## How was the CTF conducted ?

The CTF was conducted online, challenges were hosted on the server.
There were 3 levels in the CTF, this CTF mainly concentrated on web challenges.
It was a elemination competition, so we need to qualify previous levels in order to advance....
The CTF ranks are decided on number of flags submitted by a user, if the numbers are same, the player who submitted the flags before are considered as winners

## Solutions 

The web challenges were intermediate level, 
some of the web attacks I exploited here were sql injection, Rate Limit Bypass, jku claim misuse, etc

###  SQLi 

- It's basically vulnerable where the server doesn't sanitize user input and the user can modify the queries
  - For e.g. : 
  - `$sql = "SELECT * from Users where uname = '$username' and password = '$password'"` (Let's take this as our sql query)
  - In the login form the user can update the sql query as : `" 1 OR 1 == 1 -- `
  - Now the updated query in the backend would be : `"SELECT * from Users where uname = " 1 OR 1 == 1 -- and password = '$password'" `
  - Now since `--` in SQL are comments the rest of the query after that is nothing but comment
  - as `1 OR 1 == 1` is always true the SQL will return true and the user can bypass the admin account without any password

- There are different types of SQL Injections,
  1. Error-based SQLi
  2. Union-based SQLi
  3. Blind SQLi, etc
 - SQLi itself is a big topic you can learn it's basics from here : `https://www.youtube.com/watch?v=wcaiKgQU6VE`

### Rate Limit Bypass

- Rate Limit is what the server set to control `number of request` per user
- This was a good option, later they were used in `OTP Auth` so user cant bruteforce the OTP
- The hackers then used `VPN, proxies` to bypass this.....
- The request was blocked on IP, so the hackers used `VPN` to change IP after `x` number of request, and a hacker can then use this to `bruteforce OTP` and byass the `OTP Auth`
- Furether Reading - `https://huzaifa-tahir.medium.com/methods-to-bypass-rate-limit-5185e6c67ecd`
- Video - `https://www.youtube.com/watch?v=TPvYByZPOHA`

### Jku claim misuse

- I had exploited this attack previously on a HTB machine
- Read the blog from here : `https://gist.github.com/heapbytes/31ab6480fd368d7d1e61be29ba738a61`

### Buffer Overflow and Pickle Python Vulnerability

- I've made Video POC. for both of them at the time of submission : `https://github.com/heapbytes/Sainya_Ranakshetram_CTF`

## Final thoughts

Well I had fun playing this CTF, learned a lot, and hope someday can report it in real world bounty programs
The goal of CTFs also develops the methodology of recognizing bugs, which part of code mightbe vulnerable, etc.
Not all vulnerability are same some may occur after update/patch of the previous version, the main thing is one is updated about the latest exploits.
The CTF is a annual event so you can register and explore, official url : https://www.sainya-ranakshetram.in/


## References

- YouTube
- Medium blogs
- Portswigger
- Python Documentation
- Wikipedia




