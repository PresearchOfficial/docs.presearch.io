---
description: >-
  We recommend always backing up your private key of your node, but here is an
  alternative to doing so
---

# Alternative to Backing up nodes

In some cases, a node operator may lost access to their node's identity (the public/private key pair created when a node starts for the first time). Since the Presearch network is decentralized, it has no knowledge to your private key, which means that there is no way to recover the key unless you have backed it up.

While we recommend every node operator backup their public and private key-pair (instructions here), we understand that some providers (like FLUX) don't persist keypairs or make it possible to access them to back them up. If you have a node with an old stake that is grandfathered in (meaning new nodes require higher stakes), this can lead to your new nodes requiring higher PRE stakes than the old nodes you lost access to.

In order to accommodate these use cases and provide greater flexibility to our community, we are implementing a mechanism to "migrate" stakes from a previous, disconnected node, to a new node when it first registers on the network. This will allow you to more easily migrate from an old server to a new server without having to backup your keys, so long as you are okay with the node's stats starting over as a new node.

At a high level:

1. As long as you don't delete your node in your Presearch account or modify the stake (even if the node is disconnected or you've lost your keys), you'll be able to migrate your grandfathered stake to a new node.
2. If you're running on a Flux from before July 1, 2022, you'll need to [update your Flux app](../vps-setup/running-a-node-on-fluxos/) in order to turn on this migration feature.
3. The current mechanism for backing up your node's keys and restoring on another server still works and is required if you want to continue with your node's same identity, stats, and earning history after migration. This new mechanism is simply available as a convenience for those who don't have access to the node's public/private keys or don't want to deal with the hassle of backing them up and just want to migrate their old grandfathered in stake to a new node.

Essentially, on the startup of a node that you currently have setup, you need to use add the following new environment variables to your startup command beside where you add your registration code :

`-e STAKE="disconnected:oldest,wallet:minimum" -e ALLOW_DISCONNECTED_STAKE_TRANSFER_AFTER="30m"`

The STAKE parameter above says "if there's a disconnected node, migrate the stake from the oldest created node that is currently disconnected" (`disconnected:oldest`), and if there isn't a disconnected node with a stake then stake the current minimum stake from my wallet".\
\
You can alternatively just specify `STAKE="disconnected:oldest"` if you only want to migrate the Stake.

The `ALLOW_DISCONNECTED_STAKE_TRANSFER_AFTER="30m"` says that on the node it is added to, do NOT allow the stake to be migrated to another node unless it has been disconnected for at least 30 minutes. This prevents a stake from being accidentally migrated when a node is temporarily disconnected from the network due to a rebalance, a short network disruption, or a maintenance. This setting is optional, and all nodes have this delay turned OFF by default, meaning that their stakes can be migrated away anytime they are disconnected and a new node starts that specifies `STAKE="disconnected:oldest"`&#x20;

The full startup command to specify all of the above parameters will then look like this (replacing `$YOUR_REGISTRATION_CODE_HERE` with the registration code from your dashboard).

{% tabs %}
{% tab title="Linux/Mac/PREberry/Windows-Powershell" %}
`docker stop presearch-node ; docker rm presearch-node ; docker stop presearch-auto-updater ; docker rm presearch-auto-updater ; docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --cleanup --interval 900 presearch-auto-updater presearch-node ; docker pull presearch/node ; docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION_CODE=$YOUR_REGISTRATION_CODE_HERE  -e STAKE="disconnected:oldest,wallet:minimum" -e ALLOW_DISCONNECTED_STAKE_TRANSFER_AFTER="30m" presearch/node ; docker logs -f presearch-node`
{% endtab %}

{% tab title="Windows-Command line" %}
`docker stop presearch-node & docker rm presearch-node & docker stop presearch-auto-updater & docker rm presearch-auto-updater & docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --cleanup --interval 900 presearch-auto-updater presearch-node & docker pull presearch/node & docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION_CODE=$YOUR_REGISTRATION_CODE_HERE  -e STAKE="disconnected:oldest,wallet:minimum" -e ALLOW_DISCONNECTED_STAKE_TRANSFER_AFTER="30m" presearch/node & docker logs -f presearch-node`
{% endtab %}
{% endtabs %}

