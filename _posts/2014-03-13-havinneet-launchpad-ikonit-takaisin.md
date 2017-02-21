---
layout: post
status: publish
published: true
title: Hävinneet Launchpad ikonit takaisin
image:
  file: /assets/img/posts/macbook-air.jpg
author:
  display_name: Jarkko
  login: Jarkko
  email: jarkko@splatweb.net
  url: http://jarkkotervonen.com/
date: '2014-03-13 22:11:24 +0200'
date_gmt: '2014-03-13 20:11:24 +0200'
categories:
- Tekniikka
- Ohjelmat
tags:
- os x
- launchpad
- dock
- ikonit
- mavericks
comments: []
---
Jonkun aikaa ihmetellyt minne kaikki ikonit ovat hävinneet OS X:n Launchpad:lta. Ratkaisu löytyi [Applen Support -keskustelualueelta](https://discussions.apple.com/thread/5476991). Eli ``~/Library/Application Support/Dock`` hakemistosta pitää poistaa kaikki `*.db` -tiedostot ja tämän jälkeen käynnistää uudelleen Dock. Eli se tapahtuu Terminaalin kautta kirjoittamalla seuraavat kaksi komentoa:

```
rm ~/Library/Application\ Support/Dock/*.db
killall Dock
```

Hetken kuluttua ikonit ilmestyvät takaisin Launchpadille.