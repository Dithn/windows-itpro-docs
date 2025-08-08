---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Email encryption

Email encryption allows users to secure email messages and attachments so that only the intended recipients with a digital identification (ID), or certificate, can read them<sup>[\[8\]](../conclusion.md#footnote8)</sup>. Users can also *digitally sign* a message, which verifies the sender's identity and ensures the message hasn't been tampered with.

The new Outlook app included in Windows 11 supports various types of email encryption, including Microsoft Purview Message Encryption, S/MIME, and Information Rights Management (IRM).

When using Secure/Multipurpose Internet Mail Extensions (S/MIME), users can send encrypted messages to people within their organization and to external contacts who have the proper encryption certificates. Recipients can only read encrypted messages if they have the corresponding decryption keys. If an encrypted message is sent to recipients whose encryption certificates aren't available, Outlook asks you to remove these recipients before sending the email.

[!INCLUDE [learn-more](learn-more.md)]

- [S/MIME for message signing and encryption in Exchange Online](/exchange/security-and-compliance/smime-exo/smime-exo)
- [Get started with the new Outlook for Windows](https://support.microsoft.com/topic/656bb8d9-5a60-49b2-a98b-ba7822bc7627)
- [Email encryption](/purview/email-encryption)
