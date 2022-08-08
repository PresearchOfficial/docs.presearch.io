---
description: >-
  How to insure that your node will be grandfathered in for minimum stake
  increases when running on Flux
---

# Flux Node Grandfathering

If you're wondering how to run a node on Flux, you can see the full tutorial below 👇

{% content-ref url="./" %}
[.](./)
{% endcontent-ref %}

Presearch nodes are identified by a public/private keypair that is generated the first time the node starts. The FLUX doesn't currently support persistent storage of these keys, however, which means every time a new FLUX instance launches, it connects to the Presearch network as a NEW node, and not the original node. This can cause some problems, for example, if a previous FLUX instance was running with a PRE stake of 2,000 PRE, but the minimum stake for new nodes has increased to 4,000 for all new nodes.

In order to accommodate these use cases and provide greater flexibility to our community, Preseach has implemented a mechanism to "migrate" stakes from a previous, disconnected node, to a new node when it first registers on the network. This will allow you to more easily migrate from an old server to a new server without having to backup your keys, so long as you are okay with the node's stats starting over as a new node. This means that as long as you don't delete your node in your Presearch account or modify the stake (even if the node id disconnected or you've lost your keys), you'll be able to migrate your grandfathered stake to a new node, even after the increase in minimum stake takes place.

### **Flux Nodes**

Before this update, users had to [backup their public/private keypair](../../backing-up-and-migrating-nodes/) and migrate it to the new server instance anytime to preserve a grandfathered node stake from the old node if that staking level was no longer available. This is not currently possible with Flux, so we've added an ability to automatically migrate the stake from an old, disconnected Presearch node to a new node when it first joins the network.

**As long as users don’t manually unstake from a disconnected node or delete it from the node dashboard then this function works when a new node spawns.** Once a new node is launched with the new parameters, it will unstake from the old, disconnected node and automatically stake the migrated amount on the newly launched node. This means the new node will be able to run with the previous stake after it is migrated . **If you are currently running a node dApp on the Flux network you need to update your app** according to the below instructions.\


**Updating an app on FluxOs does two things**

1. Allows you to receive the grandfather status on your node when Presearch increases the minimum stake.
2. Allows nodes that are automatically shut off to have the PRE automatically transferred to a new node when it is spawned.

This is clearly a massive benefit to the user experience, as users currently have to login to unstake and stake within the dashboard to keep earning rewards on nodes run on Flux (no longer necessary). Additionally, this new mechanism will allow FLUX node operators the ability to maintain grandfathered status for the amount of nodes they are currently running at the time of any stake increase.&#x20;

### **How to update a Presearch node on Flux:**

1- Open your Zelcore multi asset crypto wallet platform and login in your account.

_2- Open your browser and g_o to FluxOS network website. [https://home.runonflux.io](https://home.runonflux.io/)

![](https://miro.medium.com/max/1400/1\*CBfqLJmWz4qC4H7tGJ7MNA.png)

3- Press ZelId icon on FluxOs network website. This will open Zelcore with a message to sign. Sign it & open the browser again and you will be already logged in.&#x20;

4- In the browser, press Apps -> Global Applications -> in the My Apps tab and you should see your app.

![](https://miro.medium.com/max/1400/1\*p383kAAzvsPdKcghJLOcYw.png)

5\. Press Manage and Update Specifications.

![](https://miro.medium.com/max/1400/1\*vWHO45Xo1cqZOysXPW-Xwg.png)

You can scroll down and see the environment values of your app where your node key, and other node startup values are. **If you are updating an old version of the app running on the network this is where you will have to introduce changes.**

Old environment value for a node running on FluxOs:

```
[”REGISTRATION_CODE=$YOUR_REGISTRATION_CODE_HERE”]
```

**New environment value for nodes running on FluxOS.**

Make sure to update $YOUR\_REGISTRATION\_CODE\_HERE with the code from the platform.

```
[“STAKE=disconnected:oldest,wallet:minimum”,”ALLOW_DISCONNECTED_STAKE_TRANSFER_AFTER=30m”,”REGISTRATION_CODE=$YOUR_REGISTRATION_CODE_HERE”]
```

6\. Press Compute update Message, scroll down again

* Sign with Zelcore
* after signed, press Update Flux App
* scroll down again, pay with Zelcore!

![](https://miro.medium.com/max/1400/1\*MpqtefYAkiEEpMpu72eqVg.png)

7\.  After you have paid the app update, it will take few minutes for you to see it updated on Global Apps.&#x20;

That's it! you'll have to top up payments to keep your nodes running, but you can say goodbye to logging into the dashboard to update your node stake and say hello to grandfather status!
