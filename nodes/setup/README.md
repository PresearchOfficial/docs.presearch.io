---
description: Get your node up and running in just a few minutes on your computer.
---

# ⚙ Node Setup Instructions

We're excited to have you be a part of the future of search. Tens of thousands of nodes are already being operated by Presearch node operators and these nodes provide the infrastructure for the main Presearch search experience, which can be searched via: [https://presearch.com ](https://presearch.com)

## General assumptions

* Running a node is recommended on computers powered on 24/7 due to uptime score statistics.
* Installation or management of a node can be done over any operating system (Windows, Mac, Linux, other of your choice) as long as you can access the underlying docker application
* There is no limit for number of nodes one account could operate
* There is no preferred setup as the main goal of the project is to support decentralization

## Installation options

If you have any questions, you can join our helpful [nodes telegram group](https://t.me/PresearchNodes) or [discord #node](https://discord.presearch.com).

Before you continue the node setup process, it is good to decide where your node would be running. Typical setups are following:

* **VPS - Virtual Private Server** runnng Linux operating system directly utilizing native **Docker** application
  * Cons - can be costly, need to select a cost-friendly provider or free-tier service
  * Pros - runs within cloud or datacenters, no electicity bills
* **Home computer** running Windows or Mac operating system with [Docker Desktop](https://www.docker.com/products/docker-desktop) application
  * Cons - computer needs to be running 24/7, electricity bills, utilizes your network
  * Pros - can be executed almost immediately,&#x20;
* **PREberry** (or Raspberry Pi models 3 or 4)
  * Cons - utilizes your network
  * Pros - minimal power consumtion
* **Decentralized container solution** like ThreeFold.io with prebuilt Presearch nodes
  * Cons - harder to obtain, limited support from Presearch
  * Pros - inovative, decentralized, less costly, no electricity bills

### Required toolset

If you prefer to use your home computer, installation is done locally

* Windows - Powershell or Command Line
* Mac - Terminal or any other console application
* Linux - Console or any other similar application

If you prefer to use VPS machine, installation is done over SSH client application

* Windows - Putty or any other of your choice
* Mac - Terminal or any other of your choice
* Linux - Console or any other of your choice

### Presearch Tutorial

Please refer to the subchapter dedicated for each type of installation:

* Setup Nodes Trough VPS
  * [Running a Node on AWS](../vps-setup/aws.md)
  * [Running a Node on Racknerd](../vps-setup/running-a-node-on-racknerd.md)
  * [Running a Node on Azure](vps-setup/azure.md)
  * [Running a Node on Oracle Cloud Infrastructure](broken-reference)
  * [Running a Node on Linux VPS](../vps-setup/linux-vps.md)
* [Running a Node on ThreeFold](../vps-setup/threefold.md)

### Generic setup steps

1\. Install [Docker](https://docs.docker.com/get-docker/) \[Linux/PREberry] or [Docker Desktop](https://www.docker.com/products/docker-desktop) \[Windows/Mac] on your target machine of your choice (see the options above)

2\. Get your node registration code at [https://nodes.presearch.com/dashboard](https://nodes.presearch.com/dashboard).

<div align="center">

<img src="../../.gitbook/assets/image (10) (1) (1).png" alt="">

</div>

3\. Run the node start commands below in your terminal to install your node \
\[ See tutorials for how to open terminal on [Mac](https://www.howtogeek.com/682770/how-to-open-the-terminal-on-a-mac/) & [Windows](https://www.wikihow.com/Open-Terminal-in-Windows) ]

Copy/Paste the operating-system-specific command below into your terminal:

{% tabs %}
{% tab title="Linux/Mac/PREberry/Windows-Powershell" %}
`docker stop presearch-node ; docker rm presearch-node ; docker stop presearch-auto-updater ; docker rm presearch-auto-updater ; docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --cleanup --interval 900 presearch-auto-updater presearch-node ; docker pull presearch/node ; docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION_CODE=$YOUR_REGISTRATION_CODE_HERE presearch/node ; docker logs -f presearch-node`
{% endtab %}

{% tab title="Windows-Command Line" %}
`docker stop presearch-node & docker rm presearch-node & docker stop presearch-auto-updater & docker rm presearch-auto-updater & docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --cleanup --interval 900 presearch-auto-updater presearch-node & docker pull presearch/node & docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION_CODE=$YOUR_REGISTRATION_CODE_HERE presearch/node & docker logs -f presearch-node`
{% endtab %}
{% endtabs %}

**IMPORTANT:** You need to insert your registration code from step #2 above into the script by replacing the text`$YOUR_REGISTRATION_CODE_HERE`with your actual registration code. So, for example, if your registration code is `XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX` then the final command would contain the text `REGISTRATION_CODE=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX` .

The above command installs two services on your computer, the _**presearch-node**_ and the _**presearch-auto-updater**_**,** and configure both of them to be always running in the background.&#x20;

The _presearch-node_ actually runs the decentralized search software, whereas the _presearch-auto-updater_ is responsible for automatically upgrading the _presearch-node_ to the newest versions when released to ensure the node stays up to date and can continue to connect to the Presearch network.

### Common issues

* Executig installation under wrong environement
  * Using Linux  / Mac / Windows - Powershell commands under Windows - Command Line and  vice-versa
* Typo with registration code
  * API key being pasted instead of registration code
  * blank space between = and code itself
  * forgotten $ right after =
  * excluded part of registration code / omiited characters
  * remove part of the installation instruction (ea. "presearch/node" after the code)

## Running Searches

Keep an eye on the running node output and you’ll eventually see incoming searches (“Success! ...”). You can run searches yourself at [https://testnet-engine.presearch.com](https://testnet-engine.presearch.com), though keep in mind these will be distributed across all nodes in the Testnet, not just yours.

![](<../../.gitbook/assets/image (11) (1) (1).png>)

## Managing your Node

The command in the setup instructions configured your node to run as a background service. This means you can close your terminal and it will continue running as long as your system is up and haven't manually stopped your node.&#x20;

If you would like to see the output of your node at any point you can run the following command:

**See current node output:**\
`docker logs -f presearch-node`

To stop your node and the _presearch-auto-updater_ manually, run the following commands in your terminal:

**Manually stop your node:**

`docker stop presearch-node`\
`docker stop presearch-auto-updater`

To restart a manually-stopped node, run the following command:

**Restart your stopped node:**\
`docker start presearch-auto-updater`\
`docker start presearch-node`

If you would like to see if your node or the presearch-auto-updater are running, run the following command:\
\
**Check if the node services are running:**\
`docker ps`&#x20;

Finally, if you run into any problems with your node, you can always _run the installation script again_ from the [setup instructions](./) section if needed. Your node identity will be preserved, but should will get your node upgraded, reinstalled, and over most configuration issues you may encounter.

## Hardware Specification

1. Docker image is only for 64bit architectures like x64 / ARM64 based CPU's for now.&#x20;
2. Raspberry Pi Models 3/4 are also supported when running the [64-bit Raspberry Pi operating system](https://docs.presearch.org/nodes/raspberry-pi).
3. Nodes were successfully installed on VPS machines with minimal resources:
   * 1 CPU
   * 768 MB RAM (under minimized OS editions even 512 MB RAM)
   * 10 GB storage
   * 100+ Mbit network link

{% content-ref url="vps-setup/" %}
[vps-setup](vps-setup/)
{% endcontent-ref %}

## Running Multiple Nodes

You are more than welcome to run as many nodes as you would like under your Presearch account. You can reuse the same Registration Code to launch each node, subject to the following limitations:

* You may only run one node per server at a time. Presearch will only allow one connection per public IP (v4) address at the same time, so if you want to disconnect a second node from the same IP address you’ll need to stop the other node first. IPv6 addresses are currently not supported.
* You must include a valid Registration Code on the first run of each node to initialize it and attach it to your Presearch account. When the node software runs for the first time, it creates a public/private key pair to uniquely identify your node on subsequent requests.
* You can optionally change your Registration Code at any time by clicking "Generate Replacement Code" on the [Nodes Dashboard](https://nodes.presearch.org/dashboard). Any prior nodes initialized with the old Registration Code will continue to work, but the old code will no longer be able to initialize any new nodes.
* You may not run the same node simultaneously on multiple servers. If you initialize a node and then copy the initialized node to another server (which transfers the node’s unique public/private key identifiers), this creates a copy of the same node identity on both servers. If you try to run both at the same time, the Presearch Engine will reject the second one until the first disconnects.
