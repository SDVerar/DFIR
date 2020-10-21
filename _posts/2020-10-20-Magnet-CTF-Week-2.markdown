---
layout: post
title:  "Magnet CTF: Week 2 Write Up"
date:   2020-10-20 12:00:00 -0400
categories: jekyll update
---
Week 3 of Magnets CTF event has just started so the means it is time for week 2 write up! If you missed or want to view my week 1 write up, you can visit [this link](https://sdverar.github.io/DFIR/jekyll/update/2020/10/15/Magnet-CTF-Week-1.html).

This weeks questions:

`Challenge 2 (Oct 12-18) PIP Install 30
What domain was most recently viewed via an app that has picture-in-picture capbability?
`

Tools used: Axiom Process

The first thing we need to look at is what applications support picture-in-picture capbability and what applications are installed on our device image. Doing some research finds us to a [link](https://nokiapoweruser.com/list-apps-support-oreo-picture-picture-mode-enable/) that lists out android apps the support picture in picture capability.
It lists out the following apps:

Google Maps  
WhatsApp  
Google Duo  
Google Chrome  
Facebook  
VLC  
Youtube Red  
Netflix  
Telegram  
Swiggy  
Skype  
Microsoft Edge  

Well great, my first thought is to look at Google Chrome data as it is going to be an app that frequently views domains during use and lucky for us, Chrome is installed on our device!. If we switch over to our Chrome Cache Records under Web Related in Artifacts it brings a list of 6,516 cached events obtained as seen in the image below.

![Records](https://sdverar.github.io/DFIR/Assets/cache_record.jpg)

All we need to do is reorganize our data in descending order of last visted and it brings us to the last url accessed of "http://malliesae.com/investor-page". Cutting this down to just its domain name of "maliesae.com" and input that into our challenge box gives us our correct answer for week 2!

**Post solution and learning**

There are a couple of side notes to this and one is to make sure you do not do what I did and insert the whole url instead of the domain name then get really confused and start typing common domain names. Also something that I did not know was that you can actually find where it states that Chrome supports Picture-in-Picture cabability within XML code! A new artifact I just had learned about is the recent_tasks directory under `data\system_ce\0\recent_tasks`. It list all recent tasks performed in a XML format. Looking into that can find Chrome XML data that if open you can find this line of code: "supports_picture_in_picture="true"" as shown the photo below.

![XML Data](https://sdverar.github.io/DFIR/Assets/xmldata.jpg)

 This was something that I was not aware of until afterwards thanks to some of the folks in the Magnet Discord had shared it! I am thankful for the Magnet Team for putting together an event like this so students like myself can get some expsoure to forensic tools and learn a lot about Mobile Device Forensics. That is it for week 2, still working on Week 3, it is a tough one!