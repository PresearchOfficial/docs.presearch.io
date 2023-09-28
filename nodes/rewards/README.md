---
description: Node Rewards are the rewards you receive for being a node operator
---

# 🎇 Node Rewards

## Node Staking

There are many reasons someone may want to run a node. They may be looking for financial reward, they may want to support the Presearch mission of providing community-powered, decentralized search to the world, they may want to have their own personal search experience, or they may simply want to download the software and try it out using their idle compute resources.&#x20;

If more server capacity is needed in the network, the Tokenomics Engine will increase the current payout level to incentivize more servers to join the network. If too many nodes are operating within the network and there is excess server capacity, the Tokenomics Engine will reduce aggregate rewards for node operators and will increase rewards for other behaviors within the Presearch ecosystem, such as those which increase the number of active users.&#x20;

When Node Rewards are increased, this should lead to more nodes joining the network, and when Node Rewards are decreased, this should lead to nodes leaving the network.&#x20;

While most node operators will likely keep their nodes operating continuously, since it will eventually be possible for nodes to receive higher payouts for providing more reliable uptime, Presearch expects for some nodes to also be set up to autoscale up and down in order to take best advantage of periods of elevated rewards payouts that will correspond with normal traffic fluctuations from users running searches on the Presearch search engine.

Because node operators will invest their resources in running nodes and will expect a minimum level of payout to keep the nodes running and financially viable, Presearch will need to ensure that the Node Rewards levels are transparent, published, and up-to-date.&#x20;

Presearch will provide an autoscaling pool of nodes when the network first launches as a fall-back to ensure smooth operations of the network, but maintaining this fallback will probably become unnecessary over time as the decentralized network grows and more nodes.

## **Node staking as a mechanism for allocating capacity**

There is a maximum amount of work to be performed by nodes within the Presearch network, and that amount of work is determined by the Tokenomics Engine based upon a combination of current active user search volume (drives both server demand and available ad revenue to be used for Node Rewards) and the amount of capacity node operators are willing to provide for that level of Node Rewards.&#x20;

Because total payable Node Rewards has a ceiling, this means that should too many nodes try to provide capacity to the network at any given time, there would not be enough demand for that server capacity, and the PRE rewards paid could drop to a level at which all node operators would be operating at a loss.

In order to avoid that scenario, and recognizing that there is both an upper limit to capacity demand and a lower limit to profitability for node operators, Presearch needs to prevent any situation where all node operators hit that limit at the same time and leave the network.&#x20;

The project accomplishes this goal by utilizing the staking of PRE to a node as our mechanism to efficiently allocate the amount of capacity each node is entitled to provide. Through Node Staking, node operators can reserve the right to provide a predetermined amount of capacity based upon the size of their PRE stake. This ultimately enables node operators to also secure a predetermined allocation of Node Rewards for that capacity. This means that node operators who stake more PRE are going to be more profitable than those that stake less PRE. This provides a needed mechanism for reliable node operators who are potentially running expensive, fixed server farms to commit PRE as a stake to secure stability in their Node Rewards payouts, while still allowing anyone else to operate a node but receive potentially more variable Node Rewards.&#x20;

## **No Maximum Stake**

&#x20;There is no upper limit to the number of PRE that can be staked to a node. The percentage of the Node Rewards assigned to each node increases as the number of PRE staked to that node increases, so node operators will be incentivized to stake as many PRE for their nodes as they have available in order to maximize their Node Rewards earnings.

Whereas Keyword Staking provides more access to advertising views as the amount of PRE increases, Node Staking secures the right to provide server capacity and to do work, which is then compensated in PRE. Since there is no upper limit to the amount of PRE stakeable to a node, this provides a significant incentive for node operators to acquire and stake as much PRE as possible.&#x20;

## **Minimum Stake For Node Rewards**&#x20;

For a node operator to receive Node Rewards, they will be required to stake a minimum number of PRE to their node. The minimum stake to receive Node Rewards is currently 4000 PRE, but this minimum threshold may be adjusted up or down over time.&#x20;

**Note**: Before October 9, 2021, the minimum stake was 1000 PRE, thereafter 2000 PRE. On _July 1st, 2022_ the minimum staking requirement rises to 4000 PRE. Any node still staking between 1000 - 4000 PRE may continue to keep their current stake (or higher) indefinitely as long as they don't modify it, with the following understanding:

* You may increase your stake at any time to any higher amount
* You will not be able to reduce your stake again if your new stake is still below the new minimum
* If you unstake your tokens (set a stake of '0') then your new minimum stake will be 4000.

As an example, someone staking 1000 may continue to do so indefinitely. The may increase their stake to 1001, 1002, ... 4000 as many times as they want. Once they set their stake to 1001, however, they will not be able to reduce it back to 1000. Once they stake 4001, however, they will be able to reduce down to 4000 (the new minimum stake), but now below.

This has the **effect of grandfathering** in all staking node operators with their stakes from before the change, while enabling them to increase, but not decrease, their stakes at any time.

## **Running a Node Without Staking**

Presearch currently plans to allow anyone to run a node and provide server capacity to the Presearch network, even without requiring them to stake PRE. In this case, however, they will not receive any Node Rewards - they will simply be providing free server capacity to the Presearch network.&#x20;

This may be an attractive option for someone who just wants to test out running a node before going through the full process of setting up an account, purchasing and transferring PRE, registering their node, and configuring staking. It is unlikely that non-staking nodes will be the most common use case, as most node operators will eventually want to receive Node Rewards. Having this option removes a barrier to entry, however, and provides a convenient option that could ultimately attract more overall interest to the platform. Depending upon how this feature is used, this policy may change such that all node operators may be required to provide a minimum stake in the future.&#x20;

## Node Rewards Calculation

![](https://miro.medium.com/max/1934/1\*SBKtKXcLvEOsGwxsghTIwA.png)

Node rewards are calculated based upon a combination of each node’s utilization percentage, reliability score and its staked capacity percentage (each 1/3 weight currently).

Staked capacity enables node operators to stake PRE tokens to their node and reserve the right to be rewarded at a higher level for providing their node’s capacity to the network. This can help ensure that a node remains profitable even if other lower-cost nodes come in and reduce utilization-based rewards. Also note that while staking PRE on a node is not currently required to run the node, that in order for a node to be eligible to receive any rewards, it must have at least 1000 PRE staked.

The staked capacity percentage is calculated as follows:

![](https://miro.medium.com/max/3368/1\*zPU8zYshMZBZ2Em6ikaVgQ.png)

At the moment, the _node\_actual\_capacity\_%_ is mostly based upon uptime, but this will change in the future as better mechanisms for measuring actual capacity are being developed.

The utilization percentage is calculated as follows:

![](https://miro.medium.com/max/3392/1\*04tUGdSCHvNDoYRxydZhcQ.png)

Utilization demonstrates the percentage of requests your node serves within the network, adjusted based upon how well your node is performing relative to other nodes.

The node’s reliability score (or “quality score”) is based upon a combination of the node’s uptime, latency, and query success rates. Each node will be assigned a percentile rank for each of these three metrics compared to all other nodes within the network — the higher the percentile, the higher the payouts a node operator will receive.

All of these metrics — uptime, latency, and success rate scores, as well as the node’s reliability score, staked capacity percentage, and utilization percentage are published in the recently-release [node statistics](https://presearch.medium.com/presearch-node-statistics-go-live-6386cbe41519) available in the nodes dashboard.

If you’d like to dive into the full rewards calculation, you can find it in section 7.3 of the [Presearch Vision Paper](https://presearch.io/vision.pdf). Please note that all inputs and weights are designed to be adjusted over time automatically by the Presearch’s Tokenomics Engine, so weights of different factors are always subject to evolve over time based upon supply and demand dynamics.

## How are rewards claimed? <a href="#f901" id="f901"></a>

The total number of rewards generated by your nodes is visible on the nodes dashboard, along with a “Claim” link that takes you to the node rewards claiming page.

![](https://miro.medium.com/max/3076/1\*hZhP3DMavQ-b5Qi1Fuhp4w.png)

Any accrued rewards sit in an outstanding rewards pool owned by Presearch, but by clicking the “Claim Now” button you can take ownership of those rewards from the pool and have them immediately transferred to your Presearch savings account. Until a node operator clicks the “Claim Now” button, they do not take ownership or possession of rewards from the rewards pool, allowing the node operator flexibility (for accounting and tax purposes) of how both the timing and quantity of rewards transactions within their Presearch account.

![](https://miro.medium.com/max/3104/1\*LbNlhBU9v\_HHrF42cVbWmg.png)

Once rewards are claimed, they are immediately transferred to and available in the node operator’s Presearch savings account and can then be applied as an additional stake on nodes (further increasing the node rewards payouts) or as a stake for [keyword advertising](http://keywords.presearch.org/).

We’re beyond excited to share the new node rewards system with the community, and excited for the continued evolution of the Presearch nodes platform and upcoming releases. Stay tuned for one more exciting release announcement still coming this week!

Thanks again to all of the amazing Presearch node operators for your support in helping us develop and run the node platform that powers the new Presearch decentralized search engine!

Team Presearch

## PS: Want to start running a node? <a href="#69c7" id="69c7"></a>

Head to [https://nodes.presearch.com](https://nodes.presearch.com) to learn more and join our [Nodes Telegram Community](https://t.me/PresearchNodes)

For more information about Presearch, head to our [Company Website](https://presearch.io/)

[Try Searching with Presearch](https://presearch.org/)

##
