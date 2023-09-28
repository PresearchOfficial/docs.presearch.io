---
description: >-
  Presearch Node build & install on Windows using Docker – How-to Guide with
  steps.
---

# Mechanic Joe



![Presearch Node Thecryptogarage.com](https://thecryptogarage.com/wp-content/uploads/2021/09/Presearch-Node.jpg)

This post is a guide to installing a Presearch node in Docker using Windows. This is likely to be the quickest and easiest method to get started and stand your Presearch node up.

The host being used is Windows however the environment you choose could be a local computer or Virtual Private Server (VPS). The details below are irrelevant to the environment, however, you should consider certain factors when deciding on the location of your node, most notably the computer power and your internet. The node will be scored and your earnings could be impacted if your reliability score becomes low due to factors such as the node not being available or poor internet connection.Table of Contents

* [Presearch](https://thecryptogarage.com/presearch-node-build-install-on-windows-using-docker/#presearch)
* [Hardware Requirements](https://thecryptogarage.com/presearch-node-build-install-on-windows-using-docker/#hardware-requirements)
  * [Docker](https://thecryptogarage.com/presearch-node-build-install-on-windows-using-docker/#docker)
  * [Presearch Node](https://thecryptogarage.com/presearch-node-build-install-on-windows-using-docker/#presearch-node)
* [Hardware Selection](https://thecryptogarage.com/presearch-node-build-install-on-windows-using-docker/#hardware-selection)
* [Node Requirements](https://thecryptogarage.com/presearch-node-build-install-on-windows-using-docker/#node-requirements)
* [Prepare for Presearch Installation](https://thecryptogarage.com/presearch-node-build-install-on-windows-using-docker/#prepare-for-presearch-installation)
  * [Docker Install](https://thecryptogarage.com/presearch-node-build-install-on-windows-using-docker/#docker-install)
* [Install Presearch](https://thecryptogarage.com/presearch-node-build-install-on-windows-using-docker/#install-presearch)
  * [Installation](https://thecryptogarage.com/presearch-node-build-install-on-windows-using-docker/#installation)
  * [Setting your stake](https://thecryptogarage.com/presearch-node-build-install-on-windows-using-docker/#setting-your-stake)
* [Summary](https://thecryptogarage.com/presearch-node-build-install-on-windows-using-docker/#summary)

### Presearch

This post assumes that you’re already aware of Presearch, the rewards for running a node and the considerations you should take into account when becoming a node operator. We covered earning $PRE through the search engine in a previous post [here](https://thecryptogarage.com/search-privately-online-with-a-decentralized-search-engine-and-earn-crypto-pre/).

![Presearch.org Screen Earn Crypto](https://thecryptogarage.com/wp-content/uploads/2021/09/Presearch.org-Screen-Earn-Crypto.png)

As mentioned this guide is only in support of Windows Operating System (OS) and Docker to stand up your node. You can take alternative OS options, as Docker can be installed in a variety of ways including Windows, Linux, Mac and also within cloud environments such as AWS for example.

For guidance on how to install Docker on other Operating Systems please refer to the Docker install [guide](https://docs.docker.com/get-docker/).

### Hardware Requirements

Our overall requirements are based upon the requirements of Docker and Presearch, as detailed below. Reviewing each of these is the collective minimum hardware requirements you need in the proposed setup which is:

* 4GB+ RAM \*Minimum required for Docker
* 64bit processor \*Mimimum required for Docker
* Suported Windows 10 Operating System \*Minimum required for Docker
* Virtualisation support in BIOS \*Miniumum required for Docker

#### Docker

* 64bit processor
* 4GB system RAM
* BIOS-level hardware virtualization support must be enabled in the BIOS settings
* Windows 10 or above which is still supported by Microsoft

Docker for Windows requirements can be viewed on the Docker page [here](https://docs.docker.com/desktop/windows/install/).

#### Presearch Node

The requirements are not specific by Presearch but have detailed that you do not need much disk space, memory or CPU power. For the purposes of scoping our node setup, we will have to take the minimum requirements as per Docker given above.

Presearch node requirements can be reviewed on their site [here](https://nodes.presearch.org/run).

### Hardware Selection

The requirements for hardware have been defined above. At this stage, you could decide to build and install your Presearch node on a physical machine that sits on your computer desk or virtualised in a cloud environment.

Should you choose to run Windows in a cloud environment such as AWS, the hardware requirements remains the same as those set out above or equivalent to. Pay particular attention to the cost of doing this, Linux is often the cheaper option and brings less impact to operating your node and overhead to your node management in the future.

We will cover building a server to host nodes for both Windows and Linux in the coming posts.

### Node Requirements

Before proceeding to build and install your node there are 2 other requirements which are:

* 1000 $PRE tokens to stake to each node \*Correct at time of document creation this may change at any stage
* Node registration code

In order to stake the required amount and gain a code to register your node, you will first have to signup to Presearch which you can do [here](https://presearch.org/signup?rid=2603681). Once completed you can purchase $PRE directly via the ‘Buy Tokens’ in the top right of the screen, the process is quite straightforward and quick.

You will also need a node registration code which is input into the node at the time of installation, you will need to apply for this via the ‘Nodes’ link in the top right of their page, follow through to registration which normally takes 24hrs however check back on the page via ‘Nodes’ as this is often quicker.

You should see a registration code on the node dashboard page once provided, this page can be found [here](https://nodes.presearch.org/dashboard).

![Node Registration Presearch](https://thecryptogarage.com/wp-content/uploads/2021/09/Node-Registration-Presearch.jpg)

### Prepare for Presearch Installation

By this stage you will have hopefully decided on the hardware you’re going to use either physical or virtualised. The next step is to prepare the build in order for us to install Presearch. This requirement is relatively easy to complete which is the advantage of opting for a Windows install.

Proceed to install Docker on Windows as per below.

#### Docker Install

The Docker install is well documented on the ‘Install Docker Desktop’ page found [here](https://docs.docker.com/desktop/windows/install/) however the steps required are as follows:

* Download Docker Desktop
  * Visit the Docker Desktop [page](https://docs.docker.com/desktop/windows/install/) to download the installer
* Install
  * Once downloaded open the file which will start the installation process
* Follow the prompts
  * You maybe prompted to ensure Hyper-V and WSL-2 is installed on configuration
* Run Docker
  * Open Docker from the start menu

If you experience problems or are given errors when trying to install/run Docker the most likely issues are either you do not have Virtualisation supported in your BIOS or WSL-2 is not installed on Windows.

If you need to install and update to WSL-2 follow the steps provided by Microsoft [here](https://docs.microsoft.com/en-gb/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package)

Should you need to enable virtualisation for your motherboard, use Google to search how to do this for your specific PC or motherboard as each will differ depending on make and model.

### Install Presearch

With Docker installed and running we are now ready to install Presearch itself, this process will download the Presearch software into Docker and run it. For these steps, the commands are performed in Powershell, click on the start menu and type Powershell to find the programme.

All commands below are as per the guidance given by Presearch on their install page for Windows which can be found [here.](https://docs.presearch.org/nodes/setup)

#### Installation

Copy and paste the following command into a document as you need to edit it first.

```
docker stop presearch-node & docker rm presearch-node & docker stop presearch-auto-updater & docker rm presearch-auto-updater & docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower --cleanup --interval 300 presearch-node & docker pull presearch/node & docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION_CODE=$YOUR_REGISTRATION_CODE_HERE presearch/node & docker logs -f presearch-node
```

Find the following part from within the command above and replace it with your own registration code which you registered for in the previous step.

```
$YOUR_REGISTRATION_CODE_HERE
```

Paste this into Powershell which will then download and install the Presearch node for you inside of Docker.

You can see the installed Presearch software through the UI of Docker by running the following command in Powershell

```
docker ps
```

At this stage, you should also see it connected in your node dashboard as per below.

\*This node already has staked $PRE if this was a newly installed node it would show 0

![Node Connection Presearch](https://thecryptogarage.com/wp-content/uploads/2021/09/Node-Connection-Presearch-1024x149.jpg)

#### Setting your stake

The last step to setting up the node is to stake the required minimum amount, at the time of this document that is 1000 PRE however this amount could change at any time. Once you have purchased the amount of the PRE you wish to stake, click on stake and then transfer at least the minimum to your new node to stake it, you can stake more than the minimum if you wish.

### Summary

Setting up a Presearch node is relatively straightforward and quick. You should consider the hardware and environment you wish to install and run the node. If you need to turn off the PC or you have power outages or slow internet then you are more likely to choose a third party such as AWS to host your node.

We will cover how to create a host for nodes in coming posts, if you already have a host with Docker running you do not need to have a specific host for each node you run, we run multiple nodes on the same host and also use local virtualisation to build our farm. Everyone’s requirements are different and you should take into account what is best for you and how you will manage your node going forward.

Keep up to date with announcements as Presearch will release changes. The software should automatically update keeping your node within Docker on the latest version, however, changes to the stake amount may come in the future.
