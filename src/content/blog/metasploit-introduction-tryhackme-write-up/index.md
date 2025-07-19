---
title: 'Metasploit: Introduction | TryHackMe Write-Up'
publishDate: '2025-04-30T15:30:00.129Z'
description: 'Metasploit: Introduction | TryHackMe | Write-Up by FarrosFR.'
tags: [Metasploit, TryHackMe, Write-up, Pentesting, Exploitation]
heroImage: {src: './image.png', color: '#e6e6e6'}
draft: false
comment: true
---
* * *

Here is my article on the walkthrough of free room for [Metasploit: Introduction](https://tryhackme.com/room/metasploitintro) an overview of the main components of the Metasploit Framework. I wrote this in 2025 and hope it is useful for learning about Metasploit.

## Task 1: Introduction to Metasploit

**Metasploit** is a popular exploitation framework used in penetration testing, offering tools for tasks ranging from information gathering to post-exploitation. It has two versions:

1.  **Metasploit Pro** (a commercial version with a graphical interface)
2.  **Metasploit Framework** (an open-source, command-line version).

The framework includes components like msfconsole, supporting modules (exploits, scanners, payloads), and standalone tools like msfvenom. This room will help you learn how to use Metasploit to find exploits, set parameters, and exploit vulnerable services.

> No answer needed

## Task 2: Main Components of Metasploit

Metasploit Framework is primarily interacted with through the `msfconsole`, which serves as the main interface to various modules. These modules perform tasks like exploiting vulnerabilities, scanning, and brute-force attacks. Key concepts include:

*   **Exploit**: Code that leverages a vulnerability to compromise a system.
*   **Vulnerability**: A flaw in a system that can be exploited.
*   **Payload**: Code that runs on the target system after an exploit is successful.

Metasploit modules are categorized into:

1.  **Auxiliary**: Tools for scanning, crawling, and fuzzing.
2.  **Encoders**: Encode exploits and payloads to bypass antivirus software.
3.  **Evasion**: Modules designed to avoid detection by security systems.
4.  **Exploits**: Modules categorized by the target system, like Windows, Linux, or Android.
5.  **NOPs**: No operation codes used as a buffer in exploits.
6.  **Payloads**: Codes that execute specific actions like opening a shell on the target system.
7.  **Post-exploitation**: Modules used after gaining access to a system.

These components help security professionals perform penetration tests and assess vulnerabilities. Each module serves a specific purpose, and their organization within the Metasploit framework enables effective exploitation and post-exploitation actions.

**Q1: What is the name of the code taking advantage of a flaw on the target system?**

> Exploit

**Q2: What is the name of the code that runs on the target system to achieve the attacker’s goal?**

> payload

**Q3: What are self-contained payloads called?**

> singles

**Q4: Is “windows/x64/pingback\_reverse\_tcp” among singles or staged payload?**

> singles

## Task 3: Msfconsole

The Metasploit Framework uses `msfconsole` as its main interface, which allows users to interact with its features, such as running exploits, configuring payloads, and executing other commands. It supports many common Linux commands and offers tools for penetration testing. Key features include tab completion, command history, and module context, which require parameters like `RHOSTS` and `RPORT` for exploits. Commands like `show options` and `search` help configure and find modules, while the `help` command provides details on available options. This console is an essential tool for conducting cybersecurity assessments.

I try to ran the msfconsole in Kali Linux.

![](https://cdn-images-1.medium.com/max/800/1*u9OiS4UQAbYoJcgGKb2SIQ.png)

**Q1**: How would you search for a module related to Apache?

![](https://cdn-images-1.medium.com/max/800/1*qVhKZ6n8mL4H05tXJUxz8w.png)

> search apache

**Q2**: Who provided the auxiliary/scanner/ssh/ssh\_login module?

You can run this script to find out who provided the information for auxiliary/scanner/ssh/ssh\_login

`info auxiliary/scanner/ssh/ssh_login`

![](https://cdn-images-1.medium.com/max/800/1*tnd0aCWKQJYg13qO3jpYdw.png)

> todb

## Task 4: Working with modules

This guide explains how to use Metasploit Framework for penetration testing, including launching modules, setting parameters, and managing sessions. It covers the `set` command to configure essential parameters like `RHOSTS`, `RPORT`, `LHOST`, and `LPORT`, and emphasizes checking configurations with the `show options` command. The text also discusses using global parameters with `setg`, backgrounding sessions, and interacting with them using the `sessions` command. Finally, it highlights various Metasploit prompts, such as the msfconsole, context-specific prompts, and Meterpreter shell.

You can first run this script to use the module:   
`use exploit/windows/smb/ms17_010_eternalblue`

![](https://cdn-images-1.medium.com/max/800/1*pEMQNeANyQTr2YlEvj0xhg.png)

![](https://cdn-images-1.medium.com/max/800/1*2Y7r_58CF2EC5763QUpQRA.png)

**Q1**: How would you set the LPORT value to 6666?

> set LPORT 6666

**Q2**: How would you set the global value for RHOSTS to 10.10.19.23 ?

> setg RHOSTS 10.10.19.23

**Q3**: What command would you use to clear a set payload?

> unset PAYLOAD

**Q4**: What command do you use to proceed with the exploitation phase?

![](https://cdn-images-1.medium.com/max/800/1*WKNmwX1VelSuooArrxgJiQ.png)

> exploit

## Task 5: Summary

Metasploit is a powerful framework that aids in the exploitation process, which involves identifying, customizing, and deploying exploits against vulnerable services. Throughout this training, we’ve explored the fundamental components of Metasploit and their applications. A practical example is the use of the `ms17_010_eternalblue` exploit to gain access to a target virtual machine. In subsequent sessions, we'll delve deeper into Metasploit's features, enhancing your understanding of its capabilities.

> No Answer Needed
