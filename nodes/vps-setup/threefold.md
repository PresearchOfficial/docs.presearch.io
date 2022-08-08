---
description: Deploy a Presearch Node on eVDC
---

# Running a node on ThreeFold

ThreeFold helps you to operate a Presearch Node and to power, the Presearch decentralized search engine. You can set up a node within just a few clicks. We're incredibly grateful to have them as a partner!

## [Presearch](https://library.threefold.me/info/manual/#/manual\_\_weblets\_presearch?id=presearch) <a href="#presearch" id="presearch"></a>

[Presearch](https://www.presearch.io/) is a community-powered, decentralized search engine that provides better results while protecting your privacy and rewarding you when you search. This weblet deploys a Presearch node. Presearch Nodes are used to process user search requests, and node operators earn Presearch PRE tokens for joining and supporting the network.

* Go to [https://play.grid.tf](https://play.grid.tf/) for Mainnet, [https://play.dev.grid.tf](https://play.dev.grid.tf/) for Devnet or [https://play.test.grid.tf](https://play.test.grid.tf/) for Testnet.
* Make sure you have an activated [profile](https://library.threefold.me/info/manual/#/manual\_\_weblets\_profile\_manager)
* Click on the **Presearch** tab

**Process**

![](https://library.threefold.me/info/manual/manual\_\_presearch1.png)

* Enter an instance name, specs for memory and disk size you’ll need.
* You need to sign up on Presearch in order to get your _Presearch Registration Code_. To sign up, go to [Presearch](https://presearch.org/), create your account and then head to your [dashboard](https://nodes.presearch.org/dashboard) to find your registration code.
* Choose a node to deploy your Presearch instance on.
* Either use the **Capacity Filter** which simply lets you pick a _Farm_ and _Country_, after clicking on _Apply filters and suggest nodes_ then it lists available nodes with these preferences and you pick.

![](https://library.threefold.me/info/manual/manual\_\_presearch2.png)

* Or use **Manual** and type a specific node number to deploy on.

![](https://library.threefold.me/info/manual/manual\_\_presearch3.png)

#### [Now what if you already have a Presearch node deployed somewhere and would like to migrate to Threefold?](https://library.threefold.me/info/manual/#/manual\_\_weblets\_presearch?id=now-what-if-you-already-have-a-presearch-node-deployed-somewhere-and-would-like-to-migrate-to-threefold) <a href="#now-what-if-you-already-have-a-presearch-node-deployed-somewhere-and-would-like-to-migrate-to-threef" id="now-what-if-you-already-have-a-presearch-node-deployed-somewhere-and-would-like-to-migrate-to-threef"></a>

We got you! All you need to do is:

1. Login to your old server that has your node via SSH.
2. Run `docker cp presearch-node:/app/node/.keys presearch-node-keys` in order to generate your key-pair.
3. Head to the _Restore_ tab in the Presearch weblet and paste your key-pair in the fields below and you’ll be good to deploy!

![](https://library.threefold.me/info/manual/manual\_\_presearch6.png)

After that is done you can see a list of all of your deployed instances

![](https://library.threefold.me/info/manual/manual\_\_presearch4.png)

Now head to your [dashboard](https://nodes.presearch.org/dashboard) again and scroll down to **Current Nodes**, you’ll see your newly created node up and connected!

![](https://library.threefold.me/info/manual/manual\_\_presearch5.png)

Source - [https://library.threefold.me/info/manual/#/manual\_\_weblets\_presearch](https://library.threefold.me/info/manual/#/manual\_\_weblets\_presearch)
