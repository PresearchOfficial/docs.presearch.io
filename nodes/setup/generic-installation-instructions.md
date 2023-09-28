---
description: If you do not know where to start. Here is the the default starting point.
---

# Generic installation instructions

1\. Install [Docker](https://docs.docker.com/get-docker/) \[Linux/PREberry] or [Docker Desktop](https://www.docker.com/products/docker-desktop) \[Windows/Mac] on your target machine of your choice (see the options above)

2\. Get your node registration code at [https://nodes.presearch.com/dashboard](https://nodes.presearch.com/dashboard).

<div align="center">

<img src="../../.gitbook/assets/image (10) (1).png" alt="">

</div>

3\. Run the node start commands below in your terminal to install your node \
\[ See tutorials for how to open terminal on [Mac](https://www.howtogeek.com/682770/how-to-open-the-terminal-on-a-mac/) & [Windows](https://www.wikihow.com/Open-Terminal-in-Windows) ]

Copy/Paste the operating-system-specific command below into your terminal:

{% tabs %}
{% tab title="Linux/Mac/PREberry/Windows-Powershell" %}
`docker stop presearch-node ; docker rm presearch-node ; docker stop presearch-auto-updater ; docker rm presearch-auto-updater ; docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --cleanup --interval 900 presearch-auto-updater presearch-node ; docker pull presearch/node ; docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION_CODE=$YOUR_REGISTRATION_CODE_HERE presearch/node ; docker logs -f presearch-node`
{% endtab %}

{% tab title="Windows-Command Line" %}
`docker stop presearch-node & docker rm presearch-node & docker stop presearch-auto-updater & docker rm presearch-auto-updater & docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --cleanup --interval 900 presearch-auto-updater presearch-node & docker pull presearch/node & docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION_CODE=$YOUR_REGISTRATION_CODE_HERE presearch/node & docker logs -f presearch-node`
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
**IMPORTANT:** You need to insert your registration code from step #2 above into the script by replacing the text`$YOUR_REGISTRATION_CODE_HERE`with your actual registration code. So, for example, if your registration code is `XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX` then the final command would contain the text `REGISTRATION_CODE=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX` .
{% endhint %}

The above command installs two services on your computer, the _**presearch-node**_ and the _**presearch-auto-updater**_**,** and configure both of them to be always running in the background.&#x20;

The _presearch-node_ actually runs the decentralized search software, whereas the _presearch-auto-updater_ is responsible for automatically upgrading the _presearch-node_ to the newest versions when released to ensure the node stays up to date and can continue to connect to the Presearch network.
