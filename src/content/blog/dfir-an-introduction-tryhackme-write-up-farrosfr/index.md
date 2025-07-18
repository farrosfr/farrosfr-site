---
title: 'DFIR: An Introduction | TryHackMe Write-Up'
publishDate: '2025-05-27T06:39:58.213Z'
description: >-
  Ringkasan singkat artikel tentang DFIR: An Introduction | TryHackMe Write-Up
heroImage: {src: './image.png'}
draft: false
comment: true
---
* * *

Here is my article on the walkthrough of a free room: [DFIR: An Introduction](https://tryhackme.com/room/introductoryroomdfirmodule). Introductory room for the DFIR module. I wrote this in 2025 and hope it is useful for learning about DFIR.

## Task 1: Introduction

This text introduces the importance of Digital Forensics and Incident Response (DFIR) in defensive security, emphasizing the need to prepare for security incidents despite efforts to prevent them. It outlines key topics to be covered, including the

*   Introduction to DFIR,
*   Basic concepts
*   Industry incident response processes
*   Tools used in DFIR

The goal is to provide foundational knowledge in this area and explore further resources.

> No Answer Needed

## Task 2: The need for DFIR

DFIR (Digital Forensics and Incident Response) is a field focused on collecting forensic evidence from digital devices like computers, smartphones, and media devices to investigate security incidents. It helps security professionals identify traces left by attackers, assess the scope of a breach, and restore systems to their pre-incident state.

DFIR is essential for:

1.  Detecting attacker activity and distinguishing real threats from false alarms.
2.  Removing attackers and eliminating their access to the network.
3.  Determining the scale and duration of breaches, aiding communication with stakeholders.
4.  Identifying vulnerabilities that caused the breach and improving defenses.
5.  Understanding attacker tactics to prevent future intrusions.
6.  Sharing attack information with the community.

DFIR professionals combine skills in **Digital Forensics** (identifying digital evidence) and **Incident Response** (using that evidence to address security incidents). These two areas are closely linked, with Incident Response relying on Digital Forensics insights, and Forensics guided by the scope of the Incident Response process.

**Q1**: What does DFIR stand for?

> Digital Forensics and Incident Response

**Q2**: DFIR requiz|zres expertise in two fields. One of the fields is Digital Forensics. What is the other field?

> Incident Response

## Task 3: Basic concepts of DFIR

Key practices and terminology:

1.  **Artifacts**: Pieces of evidence pointing to activities on a system, such as Windows registry keys used by attackers for persistence. Artifacts are collected from various sources like file systems, memory, or network activity during DFIR.
2.  **Evidence Preservation**: To maintain the integrity of collected evidence, it must be write-protected, and analysis should be performed on copies, not the original data. This ensures no contamination of the original evidence.
3.  **Chain of Custody**: The process of maintaining secure control over evidence to ensure its integrity. Any mishandling or unauthorized access can contaminate the evidence, weakening the investigation’s credibility.
4.  **Order of Volatility**: Digital evidence is often volatile and can be lost if not captured in time. More volatile sources, such as RAM, should be preserved before less volatile ones, like hard drives, to prevent data loss.
5.  **Timeline Creation**: After collecting and preserving evidence, creating a timeline of events is essential for understanding the sequence of actions during an incident. This timeline helps provide clarity and context to the investigation.

These concepts are foundational for DFIR professionals to efficiently and effectively handle digital evidence during an investigation.

**Q1**: From amongst the RAM and the hard disk, which storage is more volatile?

> RAM

Let’s view the attached static site to practice timeline creation and answer the first question. To do that, click on the View Site button in the top-right corner of this task.

![](https://cdn-images-1.medium.com/max/800/1*0Dp0TP95_LQ7XBNaNj1jzA.png)

You can click the log, as it can be in the spreadsheet, like the image below.

![](https://cdn-images-1.medium.com/max/800/1*Q1zm-uOfBk9RJ9cz6X8mGQ.png)

![](https://cdn-images-1.medium.com/max/800/1*AbtP3qPj0SX6MsXqNutKLg.png)

Click the row to add it to the spreadsheet, then drag and drop it in ascending order of time.

![](https://cdn-images-1.medium.com/max/800/1*RDdD0CPglGK12vmjJd6hTA.png)

Next, click the row that shows a successful login, like the image below.

![](https://cdn-images-1.medium.com/max/800/1*1Kv-yXQINZ4uGINQ2cF7og.png)

Click the red row in the image below again.

![](https://cdn-images-1.medium.com/max/800/1*MssMCUjM8yIPdi7p3pSQxQ.png)

Then, reorder everything again in ascending time, and you will get the flag. Congratulations!

> “Before I finish, I apologize for blurring the flag. I wanted you to experience taking action, not just answering the question. Thank you.”

![](https://cdn-images-1.medium.com/max/800/1*Z7H_Gj7gITI6WEJbIrrMjw.png)

**Q2**: Complete the timeline creation exercise in the attached static site. What is the flag that you get after completion?

THM(\*\*\*\_\*\*\*\*\*\*\_\*\*\*\*)

## Task 4: DFIR Tools

Several tools used in the DFIR process to enhance the capabilities and efficiency of security professionals:

1.  **Eric Zimmerman’s Tools**: Tools for forensic analysis on Windows platforms, covering areas like the registry, file system, and timelines. For more details, check out the Windows Forensics rooms.
2.  **KAPE**: A tool for automating the collection and parsing of forensic artifacts, helping create event timelines. Learn more in the KAPE room.
3.  **Autopsy**: An open-source platform for analyzing data from digital media like hard drives and mobile devices, with plugins to speed up the forensic process. The Autopsy room provides more details.
4.  **Volatility**: A powerful memory analysis tool for both Windows and Linux, used to extract information from machine memory. More information is available in the Volatility room.
5.  **Redline**: An incident response tool by FireEye for gathering forensic data from a system. The Redline room provides additional insights.
6.  **Velociraptor**: An advanced, open-source endpoint-monitoring and forensic response platform. Learn more about it in the Velociraptor room.

These tools assist in the DFIR process, and the next task will focus on understanding the Incident Response process and how Digital Forensics is integrated.

> No Answer Needed

## Task 5: The Incident Response process

Compares the IR methods defined by NIST and SANS, which are largely similar but with slight variations in step categorization. SANS uses the acronym **PICERL** for the following steps:

1.  **Preparation**: Preparing in advance for potential incidents by ensuring the right people, processes, and technologies are in place.
2.  **Identification**: Detecting an incident by analyzing indicators, eliminating false positives, and notifying stakeholders.
3.  **Containment**: Limiting the impact of the incident through short-term and long-term measures based on forensic analysis.
4.  **Eradication**: Removing the threat from the network after ensuring it is fully contained and preventing re-entry by the attacker.
5.  **Recovery**: Restoring affected services to their original state post-incident.
6.  **Lessons Learned**: Reviewing the incident, documenting findings, and improving future preparedness to handle similar incidents.

The NIST process aligns closely, though it combines **Containment**, **Eradication**, and **Recovery** into a single step, whereas SANS separates them. Post-incident activities in NIST and **Lessons Learned** in SANS are comparable. The steps are crucial for integrating Digital Forensics into effective incident handling.

Q1: At what stage of the IR process are disrupted services brought back online as they were before the incident?

> Recovery

Q2: At what stage of the IR process is the threat evicted from the network after performing the forensic analysis?

> Eradication

Q3: What is the NIST-equivalent of the step called “Lessons learned” in the SANS process?

> Post-incident Activity

## Task 6: Conclusion

In this room, we covered the following key points:

*   What DFIR is and its applications.
*   The importance of performing DFIR.
*   Basic concepts such as chain of custody, evidence preservation, and order of volatility.
*   Tools used in the industry, including EZ tools, KAPE, and Autopsy.
*   The PICERL process for incident response.

> No Answer Needed
