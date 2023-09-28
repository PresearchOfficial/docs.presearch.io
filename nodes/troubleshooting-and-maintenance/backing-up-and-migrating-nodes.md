---
description: >-
  Transfer your node to a new server, retaining the node identity, stats, and
  grandfathered status
---

# Backing Up and Migrating Nodes

Sometimes, you may want to migrate your node to a new computer or VPS, while maintaining the current node's identity, grandfathered status, and node stats.

In order to move your Presearch node to a new server, you need to back up the security keys of the node _while it’s still running_, copy them to the new server, stop the old node, run the Presearch Node Restore command on the new server, then start the node up on the new server.

For the steps below, `old-server` is the old server your node was running on, and `new-server` is the new server you are moving the node onto. Text surrounded by `{}` should be replaced with the proper actual value.

1.  Login to the `old-server` via SSH (using the Terminal on macOS/Linux or PuTTY if you are on Windows) where your node is currently running. Make a copy of the security keys

    ```bash
    docker cp presearch-node:/app/node/.keys presearch-node-keys
    ```
2.  Now stop the node running on `old-server` by running

    ```bash
    docker stop presearch-node ; docker rm presearch-node ; docker stop presearch-auto-updater ; docker rm presearch-auto-updater
    ```
3. Disconnect from `old-server` so you are back at your local command line.
4.  Download the keys backup you just made from your `old-server` to your local computer:

    ```bash
    scp -r -P {old-server-port} {username}@{old-server-ip}:presearch-node-keys ~/
    ```
5.  Upload the node security keys to `new-server` from your local computer:

    ```bash
    scp -r -P {new-server-SSH-PORT} presearch-node-keys {username}@{new-server-IP}:
    ```
6.  Now login to `new-server`:

    ```bash
    ssh -p {new-server-SSH-PORT} {username}@{new-server-IP}
    ```
7. Run `ls` to confirm that you see the folder (`presearch-node-keys`) you uploaded in step 3
8.  Let's now run the Node restore command:

    ```bash
    docker run -dt --rm -v presearch-node-storage:/app/node --name presearch-restore presearch/node ; docker cp presearch-node-keys/. presearch-restore:/app/node/.keys/ ; docker stop presearch-restore
    ```

    You'll see `docker` launch the restore code, which takes about 10 seconds to complete.
9.  Once that's done, you can launch the node similar to how you would a new node:

    ```bash
    docker stop presearch-node ; docker rm presearch-node ; docker stop presearch-auto-updater ; docker rm presearch-auto-updater ; docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --cleanup --interval 900 presearch-auto-updater presearch-node && docker pull presearch/node && docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node presearch/node && sleep 10 && docker logs presearch-node
    ```

    You should see the message `info: Node is listening for searches...` if all was started properly.
10. Refresh your dashboard, and you should see that your node is back online.

You can now remove the uploaded security key files from `new-server:`

```bash
rm -rf ~/presearch-node-keys
```

We recommend making a backup of all of your nodes' security keys.



Adapted from [https://nabeards.com/posts/moving-a-presearch-node-to-another-server/](https://nabeards.com/posts/moving-a-presearch-node-to-another-server/), which also provides direction on managing and backing up multiple nodes at once.
