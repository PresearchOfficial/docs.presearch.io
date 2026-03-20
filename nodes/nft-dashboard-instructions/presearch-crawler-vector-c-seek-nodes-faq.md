---
description: FAQ related to the new Presearch node roles.
---

# Presearch Crawler, Vector, C-Seek Nodes FAQ

1. **What can we do with the NFT acquired in the Presearch auction?**

The NFT is a license which grants the ability to run a 1:1 node. Each NFT represents a single node on the network.



2. **What are the minimum hardware requirements to run a node?**

* **Crawler Nodes (CPU)** — “Explorers of the deep, unseen web.” Role: Crawl targeted URLs across underserved/frontier verticals to expand the index.

Specs:

-RAM: 4 GB -Storage: 12 GB disk -High Speed Internet: Not Required. 30MB/s Up and Down -Dedicated IP: No -Internet always on: No



* **Vector Nodes (AI\_GPU)** — “The interpreters and translators.” Role: Generate AI summaries of crawled content for semantic understanding and vectorization.

Specs:

-GPU Card: Required, 8GB memory recommended -RAM: 10 GB -Storage: 50 GB disk -High Speed Internet: Not Required. 30MB/s Up and Down -Dedicated IP: No -Internet always on: No



* **C-Seek Nodes (AI\_CPU)** — “The crown jewel — live search brains.” Role: Convert user queries into vectors and retrieve semantically clustered results from the index and alternative providers.

Specs:

-RAM: 32 GB -Storage: 25 GB disk -High Speed Internet: Recommended (Latency could reduce amount of work rewarded) -Internet always on: Yes -Dedicated IP: No



3. **What is the required stake amount for each node?**

Crawler Nodes: 7,500 PRE Stake&#x20;

C-Seek Nodes: 20,000 PRE Stake&#x20;

Vector Nodes: 20,000 PRE Stake.



4. **What is the reward obtained for the nodes?**

20% APR for each node type (Crawler, Vector, C-seek) and this is based on the cost of running a node Which can be found on the bottom part of the spreadsheet under “Technical assumptions”

Crawler cost/month 5$ 5 x 20% / 12 = 0.083 0.083 + 5$ = 5.083$ per month

Vector cost/month 26$ 26 x 20% / 12 = 0.43 0.43 + 26 = 26.43$ per month

C-Seek cost/month 15$ 15 x 20% / 12 = 0.25 0.25 + 15 = 15.25$ per month

The calculations are based on the assumption that the node successfully completes all daily tasks, Therefore, this amount could decrease if the node fails to complete the tasks on some days.

Reward payments are processed during the first few days of each month, The amount of $ mentioned above for each node type is paid in PRE, the amount of PRE of which will also depend on the token value on the day of payment.

{% embed url="https://docs.google.com/spreadsheets/d/1Diz7esw3lF_bVNGFWP_2vY4JKGDRCs6nWbMSMJpvTlM/edit?gid=711742053#gid=711742053" %}



5. **When are node rewards paid?**

The reward calculation is done daily (every 24 hours), and will be paid monthly to the node operator (at the beginning of each month).



6. **Will staking a larger amount of Pre on a node earn me more rewards?**

No, The reward will not increase if you place more stake in a node.



7. **Will the existing nodes (legacy nodes) continue to function?**

Yes, the current nodes (legacy nodes) will continue to function without problems for now, but these nodes will also need an NFT later on to function and continue receiving rewards.



8. **Can I run multiple nodes with the same IP address?**

Yes, You can run multiple nodes with the same IP address without any problems.



9. **Can I run multiple nodes on the same machine?**

Yes, You can run multiple nodes on the same machine as long as it meets the necessary hardware requirements, Each of these nodes will need an NFT, you can also run different types of nodes on the same machine, primarily crawler nodes and C-seek nodes, And the team is also working to enable the integration of vector nodes in case the machine has the necessary GPU.



10. **Can I run multiple nodes with the same NFT?**

Yes, You can run multiple nodes with the same NFT using several low-power machines to collectively reach the daily POW, However, having multiple nodes with the same NFT will not increase the rewards.



11. **What does POW mean for a node?**

Proof of Work (PoW): Validated output based on daily required minimums (i.e, pages crawled, AI summaries generated, queries answered).



12. **How Rewards Work: Hybrid PoW / PoS / PoG?**

Node rewards are algorithmically determined by a transparent, multi-factor model:

Proof of Work (PoW): Validated output based on monthly required minimums (i.e, pages crawled, AI summaries generated, queries answered).

Proof of Stake (PoS): Minimum PRE staked to the node based on node type.

Proof of Growth (PoG): Rewards scale with Presearch revenue (driven by search volume).

Reliability & Uptime: Independently verified.

PRE Token Price Multiplier: A dynamic factor tied to ecosystem health and burn mechanics



13. **What function does each of the nodes perform?**



* Crawler Node

> Part of the engine that explores the open web

Presearch sends crawler nodes URLs collected from partners, community contributions, and user-flagged blind spots. These nodes fetch pages, download content, and extract links. Any new links are sent back to the bridge staging node, so the system never misses anything. Once a page is re-crawled, the full copy is saved into a bridge storage node, where it is ready for indexing and vectorization.



* Vector Nodes

> These nodes transform raw webpages into search engine-ready knowledge.

After the search pages are crawled and stored, the node reads each page, generates a summary, and creates a vector (a mathematical representation of the page's meaning). These summaries are stored in the index nodes to power both keyword search and AI-powered semantic search across Presearch.



* C-seek Nodes

> They help Presearch understand what users mean, not just what they type.

When a query comes, the node turns it into a vector, a mathematical representation that captures intent and meaning. They compare that meaning to a vector stored across the index nodes to find the closest semantic matches. For straightforward intent, the node can return the best results directly.



14. **Where can I get more information about this?**

You can check out our official articles on Medium and videos on YouTube.

{% embed url="https://news.presearch.io/presearch-3-0-node-orchestration-the-next-era-of-decentralized-search-ca4e67ad86a4" %}

{% embed url="https://news.presearch.io/presearch-node-nft-auction-series-ii-0e68a32cb4bd" %}

{% embed url="https://news.presearch.io/%EF%B8%8Fthe-nodeborn-6cc4f9978ba8" %}

{% embed url="https://www.youtube.com/watch?v=ljqxtLrnKzE" %}



