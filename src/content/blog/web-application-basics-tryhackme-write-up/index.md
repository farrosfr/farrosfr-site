---
title: Web Application Basics | TryHackMe Write-Up
publishDate: '2025-03-22T00:39:10.588Z'
description: >-
  Web Application Basics | TryHackMe | Write-Up by FarrosFR.
tags: [Web Basics, TryHackMe, Write-up, HTTP, Networking]
heroImage: {src: './image.png',color: '#371360'}
language: 'en'
---
Here is my writing about one of the rooms on TryHackMe, specifically [Web Application Basics](https://tryhackme.com/room/webapplicationbasics), which is part of the [Web Hacking](https://tryhackme.com/module/web-hacking) module. I will also explain how to complete the CTF in task number 10.

## Task 1: Introduction

> no answer needed

## Task 2: Web Application Overview

Q1: Which component on a computer is responsible for hosting and delivering content for web applications?

> web server

Q2: Which tool is used to access and interact with web applications?

> web browser

Q3: Which component acts as a protective layer, filtering incoming traffic to block malicious attacks, and ensuring the security of the the web application?

> web application firewall

## Task 3: Uniform Resource Locator

Q1: Which protocol provides encrypted communication to ensure secure data transmission between a web browser and a web server?

> HTTPS

Q2: What term describes the practice of registering domain names that are misspelt variations of popular websites to exploit user errors and potentially engage in fraudulent activities?

> Typosquatting

Q3: What part of a URL is used to pass additional information, such as search terms or form inputs, to the web server?

> Query String

## Task 4: HTTP Messages

Q1: Which HTTP message is returned by the web server after processing a client’s request?

> HTTP response

Q2: What follows the headers in an HTTP message?

> Empty Line

## Task 5: HTTP Request: Request Line and Methods

Q1: Which HTTP protocol version became widely adopted and remains the most commonly used version for web communication, known for introducing features like persistent connections and chunked transfer encoding?

> HTTP/1.1

Q2: Which HTTP request method describes the communication options for the target resource, allowing clients to determine which HTTP methods are supported by the web server?

> OPTIONS

Q3: In an HTTP request, which component specifies the specific resource or endpoint on the web server that the client is requesting, typically appearing after the domain name in the URL?

> URL Path

## Task 6: HTTP Request: Headers and Body

Q1: Which HTTP request header specifies the domain name of the web server to which the request is being sent?

> Host

Q2: What is the default content type for form submissions in an HTTP request where the data is encoded as key=value pairs in a query string format?

> application/x-www-form-urlencoded

Q3: Which part of an HTTP request contains additional information like host, user agent, and content type, guiding how the web server should process the request?

> Request Headers

## Task 7: HTTP Response: Status Line and Status Codes

Q1: What part of an HTTP response provides the HTTP version, status code, and a brief explanation of the response’s outcome?

> Status Line

Q2: Which category of HTTP response codes indicates that the web server encountered an internal issue or is unable to fulfil the client’s request?

> Server Error Responses

Q3: Which HTTP status code indicates that the requested resource could not be found on the web server?

> 404

## Task 8: HTTP Response: Headers and Body

Q1: Which HTTP response header can reveal information about the web server’s software and version, potentially exposing it to security risks if not removed?

> Server

Q2: Which flag should be added to cookies in the Set-Cookie HTTP response header to ensure they are only transmitted over HTTPS, protecting them from being exposed during unencrypted transmissions?

> Secure

Q3: Which flag should be added to cookies in the Set-Cookie HTTP response header to prevent them from being accessed via JavaScript, thereby enhancing security against XSS attacks?

> HttpOnly

## Task 9: Security Headers

Q1: In a Content Security Policy (CSP) configuration, which property can be set to define where scripts can be loaded from?

> script-src

Q2: When configuring the Strict-Transport-Security (HSTS) header to ensure that all subdomains of a site also use HTTPS, which directive should be included to apply the security policy to both the main domain and its subdomains?

> includeSubDomains

Q3: Which HTTP header directive is used to prevent browsers from interpreting files as a different MIME type than what is specified by the server, thereby mitigating content type sniffing attacks?

> nosniff

## Task 10: Practical Task: Making HTTP Requests

Q1: Make a **GET** request to `/api/users`. What is the flag?

![](https://cdn-images-1.medium.com/max/800/1*ryNu_9RfRi1wiRIaPbRJ7g.png)

**GET** request to `/api/users`

![](https://cdn-images-1.medium.com/max/800/1*BfJzM9C_kKCC1JtVBIDScw.png)

THM Browser

> THM{YOUHAVEJUSTFOUNDTHEUSERLIST}

Q2: Make a **POST** request to `/api/user/2` and update the **country** of Bob from **UK** to **US**. What is the flag?

Set the parameter for the country to ‘US’.

![](https://cdn-images-1.medium.com/max/800/1*Ul9olL7HLqDTOfKU0IrrZQ.png)

Parameters

![](https://cdn-images-1.medium.com/max/800/1*ERdjFQAAPG6euCNAtjOlAg.png)

**POST** request to `/api/user/2`

> THM{YOUHAVEMODIFIEDTHEUSERDATA}

Make a **DELETE** request to `/api/user/1` to delete the user. What is the flag?

![](https://cdn-images-1.medium.com/max/800/1*CBXPGZ6dmVkDrB_4lLiSIw.png)

**DELETE** request to `/api/user/1`

> YOUHAVEJUSTDELETEDAUSER

## Task 11: Conclusion

> No answer needed

* * *

Thank you for reading. I hope it was useful.
