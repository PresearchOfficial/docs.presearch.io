---
description: Setting up a node tutorial put together by TheNodeCatcher
---

# TheNodeCatcher

To see the Official Presearch Node Setup Instructions, head to:

{% content-ref url="../../nodes/setup.md" %}
[setup.md](../../nodes/setup.md)
{% endcontent-ref %}

![](<../../.gitbook/assets/vVdomoQ5 (1).jpg>)

1. Create an account on [presearch.com/signup](https://presearch.com/signup)
2. ~~Fill out the typeform~~ [~~https://presearchcommunity.typeform.com/to/UkDumktm?typeform-source=presearch.medium.com~~](https://presearchcommunity.typeform.com/to/UkDumktm?typeform-source=presearch.medium.com)~~~~
3. join the telegram https://t.me/presearch
4. wait up to 24hrs to receive approval to run a node. Once you have received confirmation, go to vultr.com and set up your VPS. Deploy a new server and choose the following options
   1. Cloud compute
   2. Newyork (NJ)
   3. Ubuntu 21.04 x64
   4. 10 GB $3.50/mo
   5. Name your server whatever you want
   6. click deploy
5. Go to [https://nodes.presearch.com/run](https://nodes.presearch.com/run)
6. The website will say to install docker, but first you need to log into terminal or putty. Once logged in, install [docker](https://docs.docker.com/engine/install/ubuntu/)
7. you will see something like this: type in `sudo apt install docker.io` then hit enter
   1. &#x20;<img src="../../.gitbook/assets/Screen Shot 2021-09-13 at 12.44.57 PM.png" alt="" data-size="original">&#x20;
8. Type in y and then hit enter. Next type in `sudo systemctl status docker` then hold down the command key on your keyboard and press c then press enter. This is to verify that docker is running properly.
9. Hold down Control key and hold down on C and then enter to exit out of checking on the status.
10. Go to https://nodes.presearch.org/dashboard and login to access your registration and API codes.
11. Go to [Node Setup Instructions](../../nodes/setup.md)
12. Scroll down until you see step 3. If you're using a mac, make sure the Linux/Mac tab is selected. Copy and paste this command into your notepad because you will need this command.
    1. `docker stop presearch-node ; docker rm presearch-node ; docker stop presearch-auto-updater ; docker rm presearch-auto-updater ; docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower --cleanup --interval 300 presearch-node ; docker pull presearch/node ; docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION_CODE=$YOUR_REGISTRATION_CODE_HERE presearch/node ; docker logs -f presearch-node`
13. replace `$YOUR_REGISTRATION_CODE_HERE`  with the registration code from step 10. Copy your new/edited command, go to the terminal and paste the command and press enter.
14. Go back to [https://nodes.presearch.com/dashboard ](https://nodes.presearch.com/dashboard)
15. Scroll down to "Current Nodes" and see if your node is appearing. If your node is there then click on stake.
16. Type in the amount you'd like to stake. The minimum is 1000 but you can do more if you'd like.
17. Type in whatever you want for the description
18. The other information is optional. Once completed, click update. Within a few minutes, your reputation show a number and continue to increase.



You can follow TheNodeCatcher on twitter here [https://twitter.com/TheNodeCatcher](https://twitter.com/TheNodeCatcher)

You can follow their blog here - [https://thenodecatcher.com/pre/](https://thenodecatcher.com/pre/)

