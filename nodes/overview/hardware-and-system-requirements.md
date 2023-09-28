---
description: >-
  Minimal recommended hardware and system resources recommendation for operating
  a node.
---

# Hardware and system requirements

## Software requirements

* **64bit enabled operating system** with virtualization capabilities to run a container
* **Docker** service to run containers (Presearch preferred and supported option)

This is by default covered in vast majority of Linux distributions. We know there are dozen of good Linux based distributions, but most used or recommended distribution is currently Ubuntu distribution for running Presearch Nodes.

{% hint style="warning" %}
Raspberry Pi Models 3/4 are also supported if they are running on a [64-bit Raspberry Pi operating system](https://docs.presearch.org/nodes/raspberry-pi).
{% endhint %}

Nodes were successfully installed on VPS machines with minimal resources:

* 1 CPU (x64 or arm64 architecture)
* 768 MB RAM (under minimized OS editions even 512 MB RAM)
* 10 GB storage
* 100+ Mbit network link

{% hint style="warning" %}
Docker image is only for 64bit architectures like x64 / ARM64 based CPU's for now.&#x20;
{% endhint %}
