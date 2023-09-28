---
description: Note this doc was created by a Presearch community member
---

# Running a node on Linux VPS



![](https://steemitimages.com/640x0/https://www.vultr.com/media/banners/banner\_800x418.png)

## Presearch Nodes: Set-Up Instructions for Linux VPS

**Presearch - The Future of Search is a Decentralized Harmonious Loop**

![presearch google sucks.jpg](https://steemitimages.com/640x0/https://cdn.steemitimages.com/DQmVrE4986k8tSFi5bepeeXqSCcNHcLTtSxbtNeYzbEeXJK/presearch%20google%20sucks.jpg)

### Overview

Don't ditch Google just for a vastly superior search experience with Presearch. When you use Presearch you also get paid to search, retain privacy, gain access to the keyword staking (free advertising) platform, and now you can run a search node to earn PRE for processing searches on the decentralized network[\
](https://www.presearch.org/signup?rid=1990186)

Getting paid in Presearch tokens for your searches is great. But the demand side for Preseach tokens is largely driven by the keyword staking advertising platform. The vision is to create a harmonious loop where users are paid PRE tokens to search and advertisers stake PRE to gain the ad space at the top of search results for staked keywords and phrases.\
Right now is a really exciting time for Presearch because the engine is polished up, and the user nodes (currently in closed beta) are about to go live to the public on January 28, 2021.

This project is really coming along. I've seen the test-net for the new engine and it's looking really good. I now much prefer Presearch to google or any other search engine and it still has so much room to develop. Read their vision paper:

[https://www.presearch.io/vision.pdf](https://www.presearch.io/vision.pdf)

First thing you may want to do is buy at least 2,000 PRE so that you can stake them to your node to start earning. If you're brand new to Crypto, you can buy PRE directly from Presearch at [https://presearch.org/signu](https://presearch.org/signup)[p\
](https://www.presearch.org/signup?rid=1990186)

If you are more experienced using exchanges or already have some cryptocurrency you can head over to KuCoin:

[https://www.kucoin.com/ucenter/signup](https://www.kucoin.com/ucenter/signup)

...to swap for PRE. Presearch token is an ERC-20 token and runs on the Ethereum blockchain, so you can also use a decentralized swapping service like UniSwap.

## Ok, Let's Set-Up Your Node

### Step I.) Deploy VPS on Vultr

We're going to run our node on a Virtual Private Server (VPS) using Vultr. Head to Vultr:

[https://www.vultr.com/](https://www.vultr.com/)

Or you can use DigitalOcean. The set-up is the same and their promotion is better right now. I think they are still giving you $100 free credit to play around with when you use this referral link:

[https://m.do.co/c/588ca27819d3](https://m.do.co/c/588ca27819d3)

[![](https://steemitimages.com/640x0/https://www.vultr.com/media/banners/banner\_800x418.png)](https://www.vultr.com/?ref=8776245)

Create and verify your account and then we will deploy a Linux Ubuntu VPS. So far the entry level VPS specs seem sufficient to run a presearch node (may need to upgrade later on). You can't use IPV6 as of now so choose cloud compute or high frequency and make sure the server size options aren't IPV6 only. Choose Ubuntu Version 18.04 and server location anywhere you think you'll get the most presearch traffic.

### Step II.) Connecting your Vultr VPS to Putty via SSH

This unrelated video has basic instructions for connecting your VPS to Putty. Follow only the steps in this video which relate to installing Putty. Ignore all the Idena stuff:

You should now have Putty installed and linked to your VPS. Login to your VPS using Putty, the default username from your Vultr VPS is root and the password and ip are also listed in the server details section of Vultr. You're going to be doing a lot of copy-pasting in and out of Putty. If you are new to this, it's important to know that passwords in Linux do not display on screen for security. Also, in Putty, you can simply right-click to paste... VERY convenient, especially when running multiple nodes and using multiple Putty connections simultaneously.

### Step III.) Run commands in Putty to install Docker and configure Linux VPS to run your node

Copy and paste the command below to install docker!

```
sudo apt update ; sudo apt upgrade -y ; sudo apt install docker.io
```

Then add your current user to the `docker` group so you can directly run docker commands:

```
sudo usermod -aG docker $USER
```

If you had any problems above, consult docker installation instructions [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/) and join the Presearch Nodes telegram channel:

[https://t.me/PresearchNodes](https://t.me/PresearchNodes)

### Step IV.) Run commands in Putty to Run Presearch Node on your VPS

For this next step, you’ll need to grab your registration code from nodes.presearch.org/dashboard in order to initialize your node.

Replace your code where it says, "$YOUR\_REGISTRATION\_CODE\_HERE"

`docker stop presearch-node ; docker rm presearch-node ; docker stop presearch-auto-updater ; docker rm presearch-auto-updater ; docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --cleanup --interval 900 presearch-auto-updater presearch-node ; docker pull presearch/node ; docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION_CODE=$YOUR_REGISTRATION_CODE_HERE presearch/node ; docker logs -f presearch-node`

### Step V.) Check Node Status & Useful Commands

#### 1.

If you would like to see the output from your node at any point, just run the following command. You can close the window at any point and your node will keep running:

`docker logs -f presearch-node`

#### 2.

Other Useful Commands

System Reboot:\
`sudo reboot`

If you have previously run a presearch node, run the following commands to stop the node:

`docker stop presearch-node`\
`docker rm presearch-node`

If you've ever run the auto-updater, you can stop it too using similar commands:

`docker stop presearch-auto-updater`\
`docker rm presearch-auto-updater`

This script checks to see if the auto-updater is installed. 1 = installed, 0 = not installed

`docker ps | grep presearch-auto-updater | wc -l`

The following script (Mac/Linux only) will return a "1" if the node is running and a "0" if it is not.\
You could put this in another script to trigger conditional logic based upon that if you wanted:

`docker ps | grep presearch-node | wc -l`

Check Node Status:

`docker ps`

`docker logs presearch-node`

For additional information check out these notes from a Presearch community member:\
[https://nodeninja.org/knowledge-base/pre/](https://nodeninja.org/knowledge-base/pre/)

## Summary

You should now have a node running on the Presearch network! Refresh the page at

[https://nodes.presearch.org/dashboard](https://nodes.presearch.org/dashboard)

[\
](https://www.presearch.org/signup?rid=1990186)

See if you're connected over there and stake your node from that page. Run your node, stake PRE to keywords to run ads (essentially free advertising to enthusiastic crypto audience), or just get paid PRE to search. Make your default search provider on Brave Browser and you are double earning BAT and PRE while you browse.

Can't say enough good things about the team as well. They have been super helpful during the closed beta. Get involved everyone! This project is a winner for decentralization and has huge potential to disrupt big tech monopolies & search suppression.

At the time of this writing development is still ongoing so everything here is subject to change or update. It's best to join the Presearch Nodes telegram group, I'll see you over there.
