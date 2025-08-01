---
title: Migrate Email Using IMAP Async with Only One Active Domain
publishDate: '2024-11-20T05:04:18.694Z'
description: 'How to Migrate Email Using IMAP Async with Only One Active Domain.'
tags: [Email Migration, IMAP, SysAdmin, Hosting, Tutorial]
heroImage: {src: './image.png',color: '#f6f7fc'}
language: 'en'
---
* * *
Here, I would like to share my experience of migrating the company’s email hosting. Previously, we subscribed to email hosting through [emailkerja.id](http://emailkerja.id) service. This service was quite good and affordable because it only limited storage capacity to 69 GB, but it provided unlimited domains and mailboxes. This allowed us to add multiple domains and mailboxes as long as the storage capacity was sufficient.

As time went by, we became more intensive in conducting email marketing to contact many companies, especially those related to EPC (Engineering, Procurement, and Construction). Therefore, we needed a more robust email server with greater capacity. This prompted us to migrate our email hosting. Of course, the main challenge we faced was how to move old emails.

After considering several options, we ultimately decided to migrate to Hostinger’s Business Starter Email service (with 10 GB of storage per account). Although we initially wanted to use Microsoft 365 or Google Workspace email hosting, we chose Hostinger for cost efficiency. If we needed more storage, we could export the data to a local file.

The migration process involves connecting the domain through DNS by using MX Record, SPF Record, DKIM Record, and DMARC Record. These can be activated as usual, but with the note that the MX Record must prioritize the new email hosting, or ideally, only the MX Record at the new hosting should be active, as email reception has shifted to the new hosting. Once the DNS is connected, we can begin the synchronization (sync) process to copy old emails from the old hosting to the new hosting.

Here is the status showing that the connection has successfully been established with Hostinger,

![](https://cdn-images-1.medium.com/max/800/1*Wy9vu_RXXHb8QZJnVQgEkA.png)

while still being connected to the previous hosting ([emailkerja.id](http://emailkerja.id)).

![](https://cdn-images-1.medium.com/max/800/1*cK4PosIgT8xROdZoN1tpNQ.png)

Once connected and with the note that the MX Record must be prioritized at the new hosting, we can access the IMAP Async process online to synchronize the emails. This process is much easier to coordinate with the company team compared to instructing colleagues to manually back up and restore emails using Outlook Classic/365. This is because not everyone has that version, considering that Outlook is usually part of an Office bundle with a license, while the New Outlook does not support this feature.

We can use the following link [https://imapsync.lamiral.info/X/](https://imapsync.lamiral.info/X/) to perform IMAP synchronization online (for accounts under 3 GB).

![](https://cdn-images-1.medium.com/max/800/1*6hAO993OOqXu2dJEMgInQw.png)

Here, we can enter the email address, password, and IMAP server details for both the source and destination mailboxes. Then, we can click “Sync” to start the synchronization process. There is a detailed log that can be scrolled down, and a percentage status is updated every 6 seconds to track progress.

Once completed, the old emails will be copied to the new email hosting. This is easy to communicate to colleagues because they can do it independently and securely without needing IT involvement, as they can input their own password.

However, if the account’s storage exceeds 3 GB, we need to access the email import feature provided by the email hosting service. Hostinger offers this feature for accounts with storage exceeding 3 GB, enabling email migration.

![](https://cdn-images-1.medium.com/max/800/1*oeQo5IIKmc1lfcmCAMYnmg.png)

Once completed, we can see that all the emails have been copied to the new hosting, and we can now use the new email hosting for sending and receiving emails.

Thank you. I hope this information is useful.
