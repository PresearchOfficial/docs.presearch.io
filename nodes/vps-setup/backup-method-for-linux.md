---
description: >-
  Following steps tends to be general backup steps for any Linux based OS
  distributions like Ubuntu, CentOS, Oracle Linux, RedHat or any other out there
  used.
---

# Backup method for Linux

## Assumptions

* You are able to connect inside your machine or VPS server over generally available SSH clients for your operating system running at your home pc or laptop (Windows, Mac, Linux or any other)
* Your node instance is running flawlessly without any troubles inside remote VPS machine or hosting provider service of your choice
* You are not hosting your node inside Docker Desktop container on a Windows or Mac machine
* You are connected into home folder and have necessary rights to read files created by docker or if you are unsure just execute with the root priviledges

## Steps to backup your node identity

### 1. Execute backup instructions inside VPS / Linux machine&#x20;

Execute following instructions right after you successfully login into your machine:

> mkdir \~/presearch-node-keys && cp /var/lib/docker/volumes/presearch-node-storage/\_data/.keys/\* \~/presearch-node-keys && ls \~/presearch-node-keys

Above instructions do:

1. create a new folder called "**presearch-node-keys**" directly in your users home folder at remote machine or VPS
2. copy identity keys (public key) **id\_rsa.pub** and (private key) **id\_rsa** into folder presearch-node-keys

![Sample output of instruction](<../../.gitbook/assets/image (16).png>)

### 2. Transfer backup under the hood

Next step is to get the backup into your home pc or laptop. Having backup resides only inside your vps machine does not guarantee you that disk or storage would never get compromised or lost for some reasons.

So to download or transfer from VPS / remote Linux based machine you could use any SFTP client of your choice. If you haven't ever done this you can try following apps:

* [**WinSCP** ](https://winscp.net/eng/download.php)for Windows
* [**CyberDuck** ](https://cyberduck.io/download/)for Windows or Mac

{% hint style="info" %}
How to use the above apps is above the scope of this tutorial, but in most cases both apps are easy to install and use without prior experience with any of them.
{% endhint %}
