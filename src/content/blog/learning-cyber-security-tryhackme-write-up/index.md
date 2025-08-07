---
title: 'Learning Cyber Security | TryHackMe Write-Up'
publishDate: '2025-05-01T16:38:34.821Z'
description: 'Learning Cyber Security | TryHackMe Write-Up'
tags: [TryHackMe, Write-up, Cybersecurity, Beginner, Learning]
heroImage: { src: './image.png', color: '#d0cfca'}
language: 'en'
---
Here’s my walkthrough article of a free room for [Learning Cyber Security](https://tryhackme.com/room/beginnerpathintro). It provides a brief introduction to several key security topics you’ll explore. Written in 2025, I hope it serves as a helpful on your cybersecurity learning journey.

## Task 1: Web Application Security

Understanding how the web works is crucial for attacking web applications. Hacking isn’t magical — it’s about knowing how a website functions and identifying weaknesses to exploit. With a solid grasp of the fundamentals, you’ll learn the techniques and tools used in hacking. Vulnerabilities in applications or systems present opportunities for attacks, as they expose weaknesses that can be taken advantage of.

Click the green “View Site” button above and learn how to hack BookFace, TryHackMe’s vulnerable social media site.

> No answer needed

**Q1**: What is the username of the BookFace account you will be taking over?

To answer this question, you need to start the site provided on the platform.

![](https://cdn-images-1.medium.com/max/800/1*Buu_j12m_gv6mbyUsZHVrw.png)

This is the username that can be used in the next page for reset the password.

![](https://cdn-images-1.medium.com/max/800/1*2mURjdeNZUomYHUpALWGJg.png)

> Ben.spring

![](https://cdn-images-1.medium.com/max/800/1*Q3Pmt1_kYnOq4DFKkyryBQ.png)

There are 10,000 possible code combinations. Trying each one individually would take very long, so try inputting a random reset code instead.

![](https://cdn-images-1.medium.com/max/800/1*UHmZEYHkF7Mln7YG6OhH8A.png)

Use the BruteForce tool with a code min (1) and max (10,000) value.

![](https://cdn-images-1.medium.com/max/800/1*88l3XwPrt2lmAS0_Xr1AxA.png)

Reset Ben’s password to continue, and then the flag will appear.

![](https://cdn-images-1.medium.com/max/800/1*dm2nKuIERVaTV1gbPpiZvw.png)

**Q2**: Hack the BookFace account to reveal this task’s answer!

> THM(************)

## Task 2: Network Security

​Networking is crucial in cybersecurity. Understanding how networks operate helps in scanning, identifying devices, and analyzing logs to monitor user activities.

Click the green “View Site” button above and see how Target was hacked on the right hand side.

> No answer needed

![](https://cdn-images-1.medium.com/max/800/1*Vys_ZPuuCeo6xkRn26hkhw.png)

**Q1**: How much did the data breach cost Target?

> $300 million

## Task 3: Learning Roadmap

The Pre-Security learning path is designed to provide the foundational technical knowledge necessary to embark on a cybersecurity career. Upon completion, you can choose to specialize in either Offensive Pentesting, focusing on ethical hacking and system exploitation, or Cyber Defense, concentrating on threat analysis and system protection. The skills acquired from these learning paths will prepare you for roles such as ethical hacker, penetration tester, or cybersecurity analyst.

> No answer needed

* * *

