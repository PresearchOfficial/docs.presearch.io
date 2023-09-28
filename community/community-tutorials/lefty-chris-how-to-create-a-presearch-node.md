---
description: This guide allows individuals to create a Presearch Node by Lefty Chris
---

# Lefty Chris - How to Create a Presearch Node

From my experience, you **do not** need a very powerful VPS for this node. You can use [Vultr](https://www.vultr.com/products/cloud-compute/), [DigitalOcean](https://www.digitalocean.com/products/droplets/), [Contabo](https://contabo.com/en/storage-vps/), or any other platform that offers a small VPS

**My VPS Specifications**: Ubuntu 20.04 (I personally like Linux servers), any server location is fine!

**Linux/Mac Users**

1. After satisfying the requirements, open Terminal
2. Type ssh root@**Your IP Address** → The IP address is from the VPS
3. Enter your VPS Password → This will connect you to the server. The password will not be shown to you when you type this into the Terminal. It’s best to copy/paste into the Terminal

**Windows**

1. After satisfying the requirements, download [PuTTy](https://www.putty.org/). PuTTy is a free SSH client
2. Open PuTTy, then type in your VPS IP Address in the **Host Name** portion of PuTTy, then click **Open**
3. Type in the username from the VPS (usually named **root**), as well as the VPS password. The password will not be shown to you in the Terminal. It’s best to copy/paste into the Terminal

>

1. Go to [Manage Nodes](https://nodes.presearch.org/login). You’ll get to the **Nodes Dashboard**. You want to send your Pre tokens from your **Metamask** to the site using **Transfer Pre**. Once selected, you will see **From Blockchain**. Click on this. You’ll see your public address, which will allow you to send your tokens to the site. Once you sent the tokens, go back to **Nodes Dashboard** and your Pre tokens will be shown in the **Available to Stake** section
2. After logging into your VPS, you’ll want to download **Docker**. You are downloading Docker **IN THE VPS**. I repeat, Docker will be downloaded **IN THE VPS**!! Docker will not be installed on your main computer! Type the following: **snap install docker**. If this doesn’t work, click on the sailboat. [![:sailboat:](https://forum.intercoin.org/images/emoji/apple/sailboat.png?v=10)](https://adamtheautomator.com/docker-ubuntu/)
3. After you install **Docker**, open an editor such as Notepad, Word (Windows), etc. You’ll need to use this command **below** in the VPS. The important part here is to **replace** where it says “$Your\_Registration\_Code\_Here” with **YOUR registration code**. You can copy this command from [here](https://docs.presearch.org/nodes/setup). Look for **Step 3** and copy the command for your Operating System, then paste into an editor. Below is what each command look like for each OS

> Windows
>
> **docker stop presearch-node & docker rm presearch-node & docker stop presearch-auto-updater & docker rm presearch-auto-updater & docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower --cleanup --interval 300 presearch-node & docker pull presearch/node & docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION\_CODE=$YOUR\_REGISTRATION\_CODE\_HERE presearch/node & docker logs -f presearch-node**

> Linux/Mac
>
> **docker stop presearch-node ; docker rm presearch-node ; docker stop presearch-auto-updater ; docker rm presearch-auto-updater ; docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower --cleanup --interval 300 presearch-node ; docker pull presearch/node ; docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION\_CODE\*=$YOUR\_REGISTRATION\_CODE\_HERE\*\* presearch/node ; docker logs -f presearch-node\***

1. Go to [Manage Nodes](https://nodes.presearch.org/login). You’ll see **Nodes Dashboard** and below is the **Registration code**. Copy and paste the code in place of “$Your\_Registration\_Code\_Here” from **Step 6**. This step is very important to create the node and **DO NOT** share your registration code to anyone!
2. Once you inserted your **Registration code** into the command from **Step 6**, copy the entire command, then go to the VPS, paste, then press enter. Let the VPS run. This should take no more than 1 minute
3. Go to [Manage Nodes](https://nodes.presearch.org/login) where your **Node Dashboard** is located. Scroll down to **Current Nodes**, then look for your node. If you do not see anything, you can click on **Active (7 days)** or **Online** to refresh your page. You’ll know if your node is created when you see a **green plug** under the **Connected** section.
4. If you see the **green plug**, then Congratulations! Now, you can look to the right and click on **Stake**. This will allow you to stake your Pre tokens into the node, as well as change the name of the node.

Check out this video on how to deploy a Presearch node [here](https://www.youtube.com/watch?v=De65YsHT9Rs)!!!

If you like more content like this, be sure to follow me on [**Twitter**](https://twitter.com/LeftyChris13)! ![:smiley:](https://forum.intercoin.org/images/emoji/apple/smiley.png?v=10)
