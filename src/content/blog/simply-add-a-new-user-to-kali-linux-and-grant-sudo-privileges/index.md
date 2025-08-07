---
title: 'Simply Add New User to Kali Linux and Grant Sudo Privileges'
publishDate: '2025-04-17T08:38:02.822Z'
description: >-
  How to Simply Add a New User to Kali Linux and Grant Sudo Privileges | FarrosFR.
tags: [Kali Linux, Linux, User Management, Sudo, Tutorial]
heroImage: {src: './image.png',color: '#acacad'}
language: 'en'
---
* * *

I want to share some basic Linux commands to add a new user via the command line. But first, we need to log in to the default user, and then you can follow these steps.

## 1. Open the Terminal

You can press `Ctrl + Alt + T` to launch the terminal.

## 2. Create a New User

sudo useradd -m username

Replace the username you need to change. The `-m` option ensures the creation of a home directory for the user.

![](https://cdn-images-1.medium.com/max/800/1*-dsr_lDTyGoyWSoRYS1G6A.png)

For example, the username I set is ‘farrosfr.’

## 3. Set a Password for the New User

sudo passwd username

Replace the username with the one that has already been created.

![](https://cdn-images-1.medium.com/max/800/1*pNl2TlqedF3_hRdASZGWjQ.png)

Type the new password for the new user and retype it until you see the message: ‘Password updated successfully’.

## 4. **Grant Sudo Privileges**

To allow the new user to execute administrative tasks, add them to the `sudo` group:

sudo usermod -aG sudo username

Don’t forget to replace the username. The `-aG` options append the user to the specified group without removing them from other groups.

![](https://cdn-images-1.medium.com/max/800/1*BvIlEz28teBul7NoET4y2w.png)

## 5. **Set the Default Shell to Bash**

sudo chsh -s /bin/bash username

Replace the username. This command changes the user’s login shell to `/bin/bash`.

![](https://cdn-images-1.medium.com/max/800/1*8oMYErwxmJCbQARoHD7kmA.png)

## 6. **Verify the New User**

id username

![](https://cdn-images-1.medium.com/max/800/1*juLvD8G4OjAkpmwmq9lwrg.png)

Explanation:

*   **uid=1001(farrosfr)**: The user ID (UID) for `farrosfr` is 1001.
*   **gid=1001(farrosfr)**: The group ID (GID) for `farrosfr` is 1001, and it's associated with the group `farrosfr`.
*   **groups=1001(farrosfr),27(sudo)**: The user `farrosfr` belongs to two groups:   
    1. `farrosfr` (group ID 1001)  
    2. `sudo` (group ID 27), which allows the user to perform administrative tasks using `sudo`.

## 7. **Switch to the New User**

su - username

![](https://cdn-images-1.medium.com/max/800/1*F2Gq41quR5oECeZXryh1EA.png)

You can also try logging in on the login panel to verify the new username.

![](https://cdn-images-1.medium.com/max/800/1*2WMesGsTg1eit7Ajk78Osg.png)

I think that’s all. Thanks for reading. I hope this can be useful.
