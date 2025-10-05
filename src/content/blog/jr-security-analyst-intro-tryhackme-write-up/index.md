---
title: 'Jr Security Analyst Intro | TryHackMe Write-Up'
publishDate: '2025-05-16T19:47:49.883Z'
description: 'Jr Security Analyst Intro | TryHackMe | Write-Up by FarrosFR.'
tags: [soc, tryhackme, write-up]
heroImage: {src: './image.png',color: '#05c7d5'}
language: 'en'
---
Here is my article on the walkthrough of a free room: [Junior Security Analyst Intro](https://tryhackme.com/room/jrsecanalystintrouxo). Play through a day in the life of a Junior Security Analyst, their responsibilities and qualifications needed to land a role as an analyst. I wrote this in 2025 and hope it is useful for learning about security analyst.

## Task 1: A career as a Junior (Associate) Security Analyst

A Junior Security Analyst, often referred to as a Tier 1 SOC Analyst or **Triage Specialist**, is a starting position in the field of cybersecurity.

### **Key Responsibilities:**

* Monitor and investigate alerts in a 24/7 SOC environment.
* Configure and manage security tools.
* Develop and implement basic Intrusion Detection System (IDS) signatures.
* Participate in SOC working groups and meetings.
* Create tickets and escalate security incidents to Tier 2 analysts or team leads when necessary.([LinkedIn](https://www.linkedin.com/pulse/junior-security-analyst-tier-1-soc-shahzad-ms-nwric))

### **Required Qualifications:**

* 0–2 years of experience in security operations.
* Basic understanding of networking (OSI or TCP/IP models), operating systems (Windows, Linux), and web applications.
* Scripting/programming skills are a plus.

### **Desired Certification:**

* CompTIA Security+

The next level for a Junior Security Analyst is to become an Incident Responder (Tier 2) and then a Threat Hunter (Tier 3) as they gain experience and expertise.

**Q1**: What will be your role as a Junior Security Analyst?

> Triage Specialist

## Task 2: Security Operations Center (SOC)

A Security Operations Center (SOC) has to monitor, detect, investigate, and respond to cybersecurity threats 24/7.

**Key Duties:**

* Monitor and investigate alerts in a 24/7 SOC environment.
* Set up and manage security tools.
* Create and implement basic Intrusion Detection System (IDS) signatures.
* Attend SOC meetings and participate in working groups.
* When necessary, open tickets and report security incidents to team leads or Tier 2 analysts.

> No Answer Needed

## Task 3: A day In the life of a Junior (Associate) Security Analyst

As a Junior Security Analyst, your role will include:

* **Monitoring Network Traffic**: Monitor alerts from IPS and IDS, and review suspicious emails to identify potential threats.
* **Extracting Forensic Data**: Analyze forensic data to detect and investigate possible attacks.
* **Using Open-Source Intelligence**: By utilizing open-source intelligence, you’ll make informed decisions to address security alerts effectively.
* **Incident Response**: You’ll investigate and manage security incidents, working through them which may take anywhere from hours to weeks, depending on the severity.
* **Threat Remediation**: After an attack, you’ll help detect, contain, and resolve threats, including addressing concerns like data exfiltration and host pivoting.

This role is challenging but rewarding, providing hands-on experience in network defense and cybersecurity.

Click on the green View Site button in this task to open the Static Site Lab and navigate to the security monitoring tool on the right panel to try to identify the suspicious activity.

![alt text](https://cdn-images-1.medium.com/max/800/1*1Rd585efrUch1LMRHehbSg.png)

From the information in the alert log, we know that there is an unauthorized connection attempt detected from a specific IP address.

**Q1**: What was the malicious IP address in the alerts?

> 221.181.185.159

![alt text](https://cdn-images-1.medium.com/max/800/1*ToTy15bYDsjXTk-I_sjFWQ.png)

We can try scanning to check that IP address.

![alt text](https://cdn-images-1.medium.com/max/800/1*9ZshfPW__uOjo0vQRv5dRw.png)

There are open-source databases, such as AbuseIPDB and Cisco Talos Intelligence, that help security analysts check the reputation and location of IP addresses.

![alt text](https://cdn-images-1.medium.com/max/800/1*ig0bckcHza2NCEeYLZvxgw.png)

Now, we need to figure out who will escalate this event.

**Q2**: To whom did you escalate the event associated with the malicious IP address?

> Will Griffin

![alt text](https://cdn-images-1.medium.com/max/800/1*uhmR5l7dDVHAHCAPqWVR_g.png)

After that, we can add the malicious IP address to the block list and capture the flag.

**Q3**: After blocking the malicious IP address on the firewall, what message did the malicious actor leave for you?

> THM{*******************}
