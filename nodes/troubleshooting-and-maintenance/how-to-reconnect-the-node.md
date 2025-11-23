---
description: Solution to reconnect your disconnected node
---

# How to reconnect the node

&#x20;Occasionally our node may disconnect for some reason: PC-VPS server problems, node version updates, etc. To reconnect the node, simply copy and paste the following script into your server and your node will be back online.

docker stop presearch-node ; docker rm presearch-node ; docker stop presearch-auto-updater ; docker rm presearch-auto-updater ; docker run -d --name presearch-auto-updater --log-opt max-size=10m --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --cleanup --interval 900 presearch-auto-updater presearch-node ; docker pull presearch/node ; docker run -dt --name presearch-node --log-opt max-size=10m --restart=unless-stopped -v presearch-node-storage:/app/node presearch/node ; docker logs -f presearch-node
