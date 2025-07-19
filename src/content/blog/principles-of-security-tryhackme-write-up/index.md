---
title: Principles of Security | TryHackMe Write-Up
publishDate: '2025-04-29T05:20:19.889Z'
description: >-
  Principles of Security | TryHackMe | Write-Up by FarrosFR.
tags: [Security Principles, TryHackMe, Write-up, CIA Triad, Cybersecurity]
heroImage: {src: './image.png', color: '#ffdc00'}
draft: false
comment: true
---
Here is my article on the walkthrough room for [TryHackMe: Principles of Security](https://tryhackme.com/room/principlesofsecurity), I wrote this in 2025 and hope it is useful for learning about principle of security.

## Task 1: Introduction

This room is about outline some of the fundamental principles of information security.

Let’s proceed!

> No answer needed

## Task 2: The CIA Triad

The CIA triad is a fundamental information security model comprising Confidentiality, Integrity, and Availability. It guides the creation of security policies to ensure that sensitive data is protected, remains accurate, and is accessible to authorized users.

*   **Confidentiality** ensures that sensitive data is protected from unauthorized access or misuse by implementing access controls and classification systems.
*   **Integrity** maintains data accuracy and consistency, preventing unauthorized or accidental modifications through methods like access restrictions, digital signatures, and hash verifications.
*   **Availability** ensures data and systems are accessible to authorized users when needed by using reliable hardware, backups, and robust security protocols to minimize downtime.

Each component is interdependent; failing to meet one can undermine the entire security framework. The CIA triad provides a continuous cycle for evaluating and prioritizing data protection needs in various contexts, from cybersecurity to physical record storage.

**Q1:** What element of the CIA triad ensures that data cannot be altered by **unauthorised** people?

> integrity

**Q2:** What element of the CIA triad ensures that data is available?

> availability

**Q3:** What element of the CIA triad ensures that data is only accessed by **authorised** people?

> confidentiality

## Task 3: Principles of Privileges

Properly defining and managing access levels in IT systems is crucial. Access is based on a user’s organizational role and the sensitivity of the data involved. Two main concepts manage this process: **Privileged Identity Management (PIM)**, which aligns user roles with system access, and **Privileged Access Management (PAM)**, which oversees the permissions those roles carry.

The **principle of least privilege** is essential — users should only have the minimal access needed for their tasks. PAM also includes enforcing password policies, auditing, and lowering risk by minimizing unnecessary privileges.

**Q1:** What does the acronym “PIM” stand for?

> Privileged Identity Management

**Q2:** What does the acronym “PAM” stand for?

> Privileged Access Management

**Q3:** If you wanted to manage the privileges a system access role had, what methodology would you use?

> PAM

**Q4:** If you wanted to create a system role that is based on a users role/responsibilities with an organisation, what methodology is this?

> PIM

## Task 4: Security Models Continued

Security models help organizations formally achieve the CIA triad — **Confidentiality, Integrity, and Availability** — by providing structured methods to control access to information systems.

*   **Bell-La Padula Model** focuses on **confidentiality** using hierarchy-based policies. It applies rules like “no write down, no read up,” suitable for hierarchical organizations (e.g., military or government) where trusted, vetted users operate. While easy to implement and mirroring real-life org charts, it assumes users are trustworthy and doesn’t fully conceal the existence of information.
*   **Biba Model** targets **integrity** with the principle of “no write up, no read down.” This means users can only write at or below their level and read above it, ensuring data accuracy over secrecy. While simple and effective for integrity, it may create operational inefficiencies and complicate access control in environments with many roles.

**Summary**: Bell-La Padula protects sensitive information in hierarchical setups, while Biba safeguards data accuracy where integrity is crucial, such as in software development. Each model has strengths and limitations, often tailored to the specific security priorities of an organization.

**Q1**: What is the name of the model that uses the rule “**can’t** read up, **can** read down”?

> The Bell-LaPadula Model

**Q2**: What is the name of the model that uses the rule “**can** read up, **can’t** read down”?

> The Biba Model

**Q3**: If you were a military, what security model would you use?

> The Bell-LaPadula Model

**Q4**: If you were a software developer, what security model would the company perhaps use?

> The Biba Model

## Task 5: Threat Modelling & Incident Response

Threat modeling is a continuous process for assessing and improving an organization’s IT security by identifying potential threats, vulnerabilities, and assessing risks. It involves preparation, identifying threats, implementing mitigations, and regular review. Frameworks like **STRIDE** help categorize threats (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege), guiding security improvements.

When security breaches (incidents) occur, a Computer Security Incident Response Team (CSIRT) manages the response through six phases: preparation, identification, containment, eradication, recovery, and lessons learned, aiming to restore operations and prevent future incidents.

**Q1**: What model outlines “Spoofing”?

> STRIDE

**Q2**: What does the acronym “IR” stand for?

> Incident Response

**Q3**: You are tasked with adding some measures to an application to improve the integrity of data, what STRIDE principle is this?

> Tampering

**Q4**: An attacker has penetrated your organisation’s security and stolen data. It is your task to return the organisation to business as usual. What incident response stage is this?

> Recovery
