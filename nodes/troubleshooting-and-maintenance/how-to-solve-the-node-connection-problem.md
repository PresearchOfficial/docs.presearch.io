---
description: Solution for node connection problems
---

# How to solve the node connection problem

&#x20;It is possible that our node may sometimes have problems connecting to the gateway and starting to receive searches, as can be seen in the following examples:

2025-09-11T08:54:23.916Z info: \[gateway.presearch.com] Connecting...\
2025-09-11T08:55:29.932Z info: \[gateway.presearch.com] Connecting...\
2025-09-11T08:56:35.950Z info: \[gateway.presearch.com] Connecting...

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

For these cases, we have some alternatives that can solve this problem.



1. **Solution 1 for Linux operating system.**

docker stop presearch-node ; docker rm presearch-node ; docker stop presearch-auto-updater ; docker rm presearch-auto-updater ; docker run -d --name presearch-auto-updater --network=host --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --log-opt max-size=10m --cleanup --interval 900 presearch-auto-updater presearch-node ; docker pull presearch/node ; docker run -dt --name presearch-node --network=host --log-opt max-size=10m -e REGISTRATION\_CODE=YOUR\_CODE\_HERE --restart=unless-stopped -v presearch-node-storage:/app/node presearch/node ; docker logs -f presearch-node



2. **Solution 2 for Linux operating system.**

docker stop presearch-node ; docker rm presearch-node ; docker stop presearch-auto-updater ; docker rm presearch-auto-updater ; docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --cleanup --interval 900 presearch-auto-updater presearch-node ; docker pull presearch/node ; docker run -dt --name presearch-node --dns=1.1.1.1 --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION\_CODE=YOUR\_CODE\_HERE presearch/node ; docker logs -f presearch-node

#### &#x20;**Copy and paste either of these two scripts into your server to resolve the node connection issue; remember to include your node's registration code to avoid problems.**

<figure><img src="../../.gitbook/assets/image (1).png" alt="" width="277"><figcaption></figcaption></figure>

#### **Note: If the first script doesn't work, you can try the second script.**



1. **Solution 1 for Windows operating system.**

docker stop presearch-node & docker rm presearch-node & docker stop presearch-auto-updater & docker rm presearch-auto-updater & docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --log-opt max-size=10m --cleanup --interval 900 presearch-auto-updater presearch-node & docker pull presearch/node & docker run -dt --name presearch-node --log-opt max-size=10m -e REGISTRATION\_CODE=YOURCODE -e STAKE=disconnected:oldest --restart=unless-stopped -v presearch-node-storage:/app/node presearch/node & docker logs -f presearch-node



2. **Solution 2 for Windows operating system.**

docker stop presearch-node & docker rm presearch-node & docker stop presearch-auto-updater & docker rm presearch-auto-updater & docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --cleanup --interval 900 presearch-auto-updater presearch-node & docker pull presearch/node & docker run -dt --name presearch-node --dns=1.1.1.1 --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION\_CODE=YOUR\_CODE presearch/node & docker logs -f presearch-node
