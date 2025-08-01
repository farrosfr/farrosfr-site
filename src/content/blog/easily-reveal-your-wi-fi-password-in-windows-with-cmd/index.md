---
title: Easily Reveal Your Wi-Fi Password in Windows with CMD
publishDate: '2025-03-28T03:23:03.921Z'
description: >-
  Easily Reveal Your Wi-Fi Password in Windows with CMD.
tags: [Windows, CMD, WiFi, Password, Tutorial]
heroImage: {src: './image.png',color: '#f0f0f0'}
language: 'en'
---
* * *

If you’ve forgotten the Wi-Fi password that was previously used on your Windows device, you can easily recover it using Command Prompt. Here’s how you can do it:

## 1\. Open Command Prompt

*   Press the **Windows** key, type “Command Prompt” or “CMD” in the search bar.
*   Right-click on “Command Prompt” and select “Run as Administrator” to open it with administrator rights.

## 2\. Display Saved Wi-Fi Network Profiles

*   In the Command Prompt window, type the following command and press **Enter**:

netsh wlan show profiles

*   This command will list all the Wi-Fi networks that your computer has previously connected to.

![](https://cdn-images-1.medium.com/max/800/1*sjIAoMnI8qGfu8IBV5CMvw.png)

netsh wlan show profiles

## 3\. View the Password for a Specific Network

*   To view the password for a specific network, type the following command, replacing `Wi-FiName` with the actual name of your network, and press **Enter**:

netsh wlan show profile name="Wi-FiName" key=clear

*   Example: If your network name is “Home123,” the command would be:

netsh wlan show profile name="Home123" key=clear

*   The information for that network will be displayed. Scroll down to the “Security settings” section and look for “Key Content.” The Wi-Fi password will be shown here.

![](https://cdn-images-1.medium.com/max/800/1*0bkruI6_anCKTv3unVmW4A.png)

From the picture above, we can see that the Wi-Fi network ‘Anti Riba’ has the password ‘antiriba’.

## Important Notes:

*   Make sure you have administrator privileges when running these commands.
*   This method only works for Wi-Fi networks you’ve previously connected to and stored on your computer.

By following these steps, you can easily find your forgotten Wi-Fi password without needing to reset your router or search for old notes.

Thank you for reading, hope it was useful.

* * *

_Article by FarrosFR_
