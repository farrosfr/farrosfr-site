---
title: Memory Analysis Introduction | TryHackMe Write-Up
publishDate: '2025-05-30T07:20:37.754Z'
description: >-
  Ringkasan singkat artikel tentang Memory Analysis Introduction | TryHackMe
  Write-Up | FarrosFR.
heroImage: {src: './image.png', color: '#e6e6e6'}
draft: false
comment: true
---
* * *
Here is my article on the walkthrough of a free room: [Memory Analysis Introduction](https://tryhackme.com/room/memoryanalysisintroduction). Learn how memory analysis helps detect threats during live investigations. I wrote this in 2025 and hope it is useful for learning about memory analysis.

## Task 1: Introduction

This session explores how memory analysis supports cyber security investigations, focusing on volatile memory and its role in identifying threats, user activity, and attack traces. It covers memory dumps, attack fingerprints, and their use in real-world cases, with interactive sections to visualize memory structures.

**Objectives:**

*   Understand memory analysis in cyber security.
*   Identify memory structure and behavior.
*   Recognize attack traces in memory.

**Prerequisites:**

*   [DFIR Introduction](https://tryhackme.com/room/introductoryroomdfirmodule)
*   [Windows Internals](https://tryhackme.com/room/windowsinternals)
*   [Linux Fundamentals](https://tryhackme.com/module/linux-fundamentals)

> No answer needed

## Task 2: Volatile Memory

Volatile memory, primarily RAM. Once the system is turned off, this data is lost, making it a priority to capture RAM early during investigations.

**Memory Hierarchy:**

*   **CPU Registers & Cache**: Fast but limited in size.
*   **RAM**: Main memory for active programs and the operating system.
*   **Disk Storage**: Slow, used for long-term storage.
*   **Virtual Memory**: Maps virtual addresses to RAM or swap space on the disk when physical memory is full.

RAM is structured into kernel space (for OS and low-level services) and user space (for user processes), with specific regions for:

*   **Stack**: Stores temporary data like function arguments.
*   **Heap**: For dynamic memory allocation during runtime.
*   **Executable (.text)**: Stores the CPU instructions.
*   **Data sections**: Stores global variables.

Memory analysis offers insights into live system activity, including:

*   Running processes
*   Open network connections
*   Logged-in users and recent commands
*   Injected code or fileless malware

Since this data disappears after shutdown, memory forensics helps collect vital information during live system investigations.

**Q1**: What type of memory is prioritized because its data disappears after shutdown?

> RAM

**Q2**: What is the slowest component in the memory hierarchy?

> disk

**Q3**: Which memory region typically contains dynamically allocated data like encryption keys?

> heap

**Q4**: What disk-based area temporarily stores RAM data when memory is full?

> swap

## Task 3: Memory Dumps

A memory dump is a snapshot of a system’s RAM at a specific moment, capturing data like running processes, network activity, and potentially sensitive information. It plays a key role in forensic analysis, malware investigations, and threat hunting. Security teams analyze memory dumps to detect unauthorized activities, while tools like Mimikatz are used to extract credentials, making memory dumps critical for defense.

Memory dumps can be created using various tools depending on the OS:

*   **Windows**: WinPmem, Sysinternals RAMMap, or built-in crash dumps.
*   **Linux/macOS**: LiME, dd, or accessing /dev/mem.

There are different types of memory dumps:

*   **Full Memory Dump**: Captures all RAM, including user and kernel space.
*   **Process Dump**: Captures memory of a single process.
*   **Pagefile/Swap Analysis**: Analyzes memory swapped to disk.

Challenges in acquiring a clean memory dump include anti-forensic techniques like hidden modules, kernel manipulation, code injection, and encrypted payloads. These require advanced methods such as memory carving and kernel-level inspection to uncover hidden activities.

**Q1**: What tool is commonly used by attackers to extract credentials from memory?

> Mimikatz

**Q2**: What type of memory dump captures all RAM, including user and kernel space?

> full

**Q3**: What Linux tool can be used to extract memory for forensic purposes?

> lime

**Q4**: Which file on Windows systems stores memory during hibernation?

> hiberfil.sys

**Q5**: What anti-forensics technique hides processes by altering kernel structures?

> DKOM

## Task 4: Memory Analysis Attack Fingerprints

Memory analysis is critical for identifying active, fileless attacks that evade disk-based forensics. Key indicators include:

### **Common Artifacts**:

*   Suspicious processes/DLLs (no disk file).
*   Process hollowing, API hooking, kernel rootkits.
*   Anomalies like mismatched PE headers or code in writable memory.

### **Credential Access (T1003)**:

In-memory extraction of credentials (e.g., LSASS dumping) and C2 communications via HTTP/DNS (decrypted configs/beacons visible in memory).

### **In-Memory Scripts (T1086)**:

Malicious PowerShell/Python scripts executed in RAM, leaving encoded commands or runtime traces.

### **Persistence Mechanisms**:

*   **Scheduled Tasks (T1053.005)**: Malicious `schtasks.exe` arguments.
*   **Services (T1543.003)**: Unusual service binaries in `services.exe`.
*   **Registry Run Keys (T1547.001)**: Malware paths in memory-cached registry hives.

### **Lateral Movement**:

*   **PsExec (T1021.002)**: Service creation/command-line args.
*   **WinRM/PowerShell (T1021.006, T1059.001)**: Remoting artifacts, base64-encoded commands.
*   **WMI (T1047)**: Suspicious `wmic` process-creation strings.

Memory forensics tools (e.g., Volatility) uncover these stealthy tactics by analyzing runtime artifacts and kernel structures.

Q1: What technique involves replacing a trusted process’s memory with malicious code?

> Process hollowing

**Q2:** Which Windows service provides PowerShell remoting?

> WinRM

**Q3:** What MITRE technique ID is associated with in-memory PowerShell execution?

> T1086

**Q4:** What command-line tool enables remote execution and is linked to lateral movement (T1021.002)?

> PsExec

**Q5:** Which MITRE technique involves setting tasks that persist through reboots (e.g., schtasks.exe)?

> T1053.005

## Task 5: Practical

Visit the site below, place the term in the proper definition, and get the flag.

[Interactive Exercise](https://static-labs.tryhackme.cloud/apps/memory-analysis-intro/)

![](https://cdn-images-1.medium.com/max/800/1*VYy0ytd_jRunjte6BIZTVw.png)

You can follow the answer below to complete it and get the flag.

Main working memory in an OS

> RAM

Contains processes launched by the user or applications

> User-Space

PsExec enables command execution on remote systems

> T1021.002 — Remote Services

Stores temporary data like function arguments and return addresses

> Stack

Captures all RAM, including user and kernel space

> Full Memory Dump

Malicious code is injected into legitimate processes

> Code Injection

> “Before I finish, I apologize for blurring the flag. I wanted you to experience taking action, not just answering the question. Thank you.”

![](https://cdn-images-1.medium.com/max/800/1*BopOLDM812wv3rTdNXF9Qg.png)

**Q1**: What is the value of the flag?

THM(\*\*\*\*\*\*\_\*\*\*\*\*\*\_\*\*\*\*\_\*\*\*)

## Task 6: Conclusion

In this room, we learned the significance of memory analysis in digital forensics, focusing on volatile memory, RAM’s role in storing active data, and its priority during incident response. We explored memory structure, forensic artifacts, and the creation of memory dumps. Additionally, we examined common attack techniques like credential dumping, DLL injection, script execution, and persistence or lateral movement, highlighting RAM’s crucial role in threat detection.

> No Answer Needed
