---
description: >-
  Following steps tends to be general backup steps for any Docker Desktop
  installation.
---

# Backup method with Docker Desktop for Windows

## Assumptions

* Your Docker Desktop is up & running without any issues
* Your node instance is running flawlessly without any troubles inside locally operated Docker Desktop for Windows
* You are not hosting your node inside any remote machine or VPS machine

## Steps to backup your node identity

### 1. Open Docker Desktop's volume&#x20;

Open following path in Windows Explorer (WinKey+E shortcut) or Run (WinKey+R shortcut):

> \\\wsl$\docker-desktop-data\version-pack-data\community\docker\volumes\presearch-node-storage\\\_data\\.keys

![Example of the output for Windows](<../../.gitbook/assets/image (17) (1) (1).png>)

### 2. Copy node's identity files

Copy identity keys (public key) **id\_rsa.pub** and (private key) **id\_rsa** into any other folder of your choice where you would like to store your node's identity

{% hint style="info" %}
If you have several nodes, perhaps consider to organize files or folders so that you would be able to idenity later which node backup files are related to specific node.
{% endhint %}
