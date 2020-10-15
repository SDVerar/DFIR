---
layout: post
title:  "Magnet CTF: Week 1 Write Up"
date:   2020-10-14 23:50:50 -0400
categories: jekyll update
---
Magnet Forensics has recently launched their [weekly CTF](https://www.magnetforensics.com/blog/magnet-weekly-ctf-challenge/) event. This is a great way for a Digital Forensics student like myself to get some exposure to tools such as Magnet Axiom, Cellebrite, Autopsy, FTK etc. Every Monday a challenge question will be posted and we are given a week to give our answer for points. After one week, that challenge will close and we will be to create our write ups on it to nab some extra points. The first few challenges will be based around an Android image that can be found [Here](https://drive.google.com/file/d/1tVTppe4-3Hykug7NrOJrBJT4OXuNOiDO/view?usp=sharing)

Week 1 Question:

`Challenge 1 (Oct 5 - 11) Mappin the Digits 20
What time was the file that maps name to IP's recently accessed?
(Please answer in this format in UTC: mm/dd/yyy HH:MM:SS)`

Tool used in this challenge: Axiom Process

First, we need to take a look at Android file systems and find out where information is stored, more particularly where names are tied to ip addresses. Through some quick Google researching, we can find that on Android file systems, it stores this information in the /etc/hosts file. Great! Now we have a strong place to look for to make our investigation much faster.

Next, we need to parse our MUS_Andriod.tar file and I will be using Axiom Process for this challenge. Once our image has been loaded, we can switch over to to file system view as seen here: 
![Search](https://neontacos.github.io/DFIR/Assets/Snip1.JPG)


Performing a quick search for 'hosts' in the file system dump will lead us to a hosts file with these details:

![hosts](https://neontacos.github.io/DFIR/Assets/snip2.JPG)

We then input our answer of 03/05/2020 05:50:18 already converted in UTC time for us and that gives our correct answer! Not too much of a challenge but keeps you on your toes.
There are many ways this could have been done and advanced tools such as Axiom Process are not even needed for a task like this. The .tar file could have been loaded into a Linux terminal and a user could have cd over to that hosts file path that way but I wanted to get some practice with using tools like Axiom. Looking forward to writing Week 2's Write up!





