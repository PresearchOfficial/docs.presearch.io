---
description: How to run a Presearch Node on a Micrsoft Azure VPS
---

# Running a node on Microsoft Azure

### **Video Tutorial**

{% embed url="https://youtu.be/lc7S3XPMXbw" %}
Video description
{% endembed %}



### **Preface**

Below we document the steps to install an Ubuntu Server 20.04 LTS virtual machine on Microsoft Azure, add Docker Community Edition and finally the Presearch node.

Right now, for a node with 1000 PREs staked on the test-net, this is not a cost-effective solution; the running cost for a single node is around EUR 7 per month. This can be brought down slightly by going for an even smaller instance but that takes a performance hit on the below setup; as described we need a single core with more than just 512Mb RAM to function best

However, it does result in a machine with optimal Reliability score and we’re in it for the long term so gaining the maximum result in PRE’s per PRE staked seems the way forward.&#x20;

### **Requirements**

* Active Azure subscription and at least $9 per node per month credit.
* Active [Node-Dashboard](https://nodes.presearch.org/dashboard) and Node registration code.
* A basic understanding of Microsoft Azure.

### **Installing an Ubuntu Server 20.04 LTS VM**

Azure lets you easily run any VM as part of their “Compute Resources”. This can be done programmatically, using ARM templates, or simply using the Azure Portal, as detailed below.

To create the Ubuntu Server platform for Docker and your Presearch node, follow these steps:

* Goto [portal.azure.com](https://portal.azure.com) and log on with your Azure account. This account should have an active Azure subscription, and the rights to create the VM.&#x20;
* From the menu on your left, select “Virtual machines”. If this option is not available, simply type “Virtual machines” in the search box on top.
* From the menu, choose “Add” and then “Virtual machine”.

![](https://lh6.googleusercontent.com/jnr0v1cUaGZh0MmVUTzdgE10xxU0cITAV9SYNfKVhJPWoT7yh2Rr-FH\_EG-SeKZTYGdPAZdYbVFpQFhC\_Jdk7esofct5lNgkkBuszSqGzuLsOqriOynzcfJxPg5UWvK9KbLE46GQ)****\
****

**The options in this first screen:**

**Subscription:** Choose any active Azure subscription connected to your account.&#x20;

**Resource group:** All the resources created for this VM (CPU, disks, virtual network,...) will be grouped under this Resource group, so it makes sense to use a separate resource group for each node since this helps when inspecting costs and performance per node.

**Virtual machine name:** Any name you like, as long as it is unique in your subscription.

**Region:** You can choose any region you want, this is the cloud. However, in this phase of the testnet all gateways are US based and from experience, nodes in US-West currently perform best.

**Availability options:** As there really is not much data to safeguard for your node and all disks in Azure offer at least some sort of redundancy, we choose “No infrastructure redundancy required” to save cost.

**Image:** Select “Ubuntu Server 20.04 LTS - Gen 1” as your base image.

**Size:** The cheapest size that still runs a Presearch node well is currently a “Standard\_B1s”, offering 1 vcpu and 1Gb of RAM. You could theoretically select the “Standard\_B1ms” which is even cheaper and offers a mere 512Mg of RAM but these did not perform as well for me, gaining a much lower Node Reliability score.&#x20;

**Note:** the price you see calculated here is going to drop a little when we go for the cheaper hard-disks below.

**Authentication type:** Because at least during setup we will have to reach the VM’s console, we need SSH access to the machine. For any publicly addressable device on the internet we should always protect access with an SSH public key. This key will be auto-generated and we will retrieve it later.

**Username:** You can leave this default (azuser) or use any name you prefer.

**SSH public key source:**  Generate a new pair, unless you have your own SSH key and prefer to use that.&#x20;

**Key pair name:** will be auto generated; leave as-is or adjust to your preferred naming scheme.

**Public inbound ports:** Allow selected ports (when the node is running you can close port 22 if you wish, we will need it now to continue the setup.

**Select inbound ports: this should be set to SSH (22).**

* Now, click “Next : Disks”, and change the default disk type to either Standard SSD or Standard HDD, the latter option being even cheaper and not impacting the node performance in this test-net phase.

![](https://lh3.googleusercontent.com/aOs1c-MErR6aHlkGbUoPELA5quecwG61S0wW1fknD60kuVB30ptQwL1yCCcmzRDB3m0aFeN5ZKPRMxjX\_UCsWjKeSEkRrv6mp9u7vnqEMD9sn3ZQaxtY22-sLlIa0NCwhP\_5uDVp)

**Selecting a cheaper disk option**\
****

* Click the “Management” tab, and ensure the checkbox “Enable auto shutdown” is unchecked, as per image below.

![](https://lh5.googleusercontent.com/YS\_i4En9ahCQCOY0XR7S3A1bsav5nNPKSXaVTRJakfe1D8xyi3n-lKnNNI8lRWdaYl8wJfUdUTxsCQpJooia-EgGr30jX51od2Vp88iG-\_lkVaUqJd3sip98pEIcKlC3S8ecs57q)

* That’s it! Now, click “Review + create”. Your selected options are checked and if all is okay, the “Create” button will become active.
* Click “Create”, and after a few seconds a pop-up will appear, offering you to download the generated keys. _****_ Click “Download private key and create resource” and a private key will be downloaded.

{% hint style="info" %}
**Note where you save this key and keep it secure! Anyone in possession of this** private key can access your server.
{% endhint %}

**Download the private key**

![](https://lh5.googleusercontent.com/tWdzED\_V\_mOjdBUG6R1ziwEp8rLOxTx0DIpBozvq3rEGRXLAmplnbPfLivWmgrlStTJORf7QO5Q94wXDucmZKU-eN0keiLd3tAC2twtAdgaATwvTWMdOIs1C94ZyIXGhsj\_gjQor)****

****\
****The system will now be deployed and a progress screen will appear. When all resources have been deployed you will be presented with a screen as below.&#x20;

![](https://lh5.googleusercontent.com/MnxzDZDXAQz-ngE0wObba7UBM5a1QispPcRSla2vRRBLyyqLhvGNiwLODAV1IG03j-xYa3oiQJuqMVYrWH6OIpZNG42jrDrA9IxVfjvl8g2ihR3K6ed6eVjefm5qeaI-UiCeiC70)

**Deployment is complete**

* Your Ubuntu Server is now running. To access it, click “Go to resource”.
* From the Virtual Machine overview screen, select “Connect” and then “SSH” from the menu.

![](https://lh5.googleusercontent.com/rOze5OC5p0tAYd-ttyxBGT3zLR3a99tDnT6CyLF0meidpgQFnczY-ngDpcrvs28v6xg5DA0NWBUcuZuKqlZfJgrjngWrSJunuOE5L5lydgtvhhxdXZsaSWkToOKwSsRhn8E3S8dD)

**Connect via SSH**

You are now shown instructions, as per image below. Note the username and IP address listed under point 4, and then use your preferred SSH client (such as Putty) to connect to the new virtual server.

![connect via SSH instructions](https://lh4.googleusercontent.com/aDNRLkFqokwJiT4GIAG8nRnatn88bt7ikrIUJQzmJ10eCbHbL4sh4f0TPg10FIr3NIl6IVgzbN-wGz8rT3a\_-11freo-llfSZ25X-CteQ6A2D2nSgHrfTyCHYTv6u7ks6clgPcmj)

From there, continue as with a standard Ubuntu VM below.

## **Installing Docker on Ubuntu Server 20.04 LTS**

**First, make sure your Ubuntu Server is up-to-date, and install supporting libraries needed for Docker.**

```
sudo apt update && sudo apt upgrade -y
sudo apt install apt-transport-https ca-certificates curl gnupg-agent software-properties-common -y
```

**Add the relevant Docker Community Edition repository, and refresh the repository cache.**

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
```

**Then, install Docker CE and add your user to the Docker group (replace \[username] below with your Ubuntu username).**

```
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
sudo usermod -aG docker [username]
```

Now log-out and login again to ensure your default user has been added to the docker group.

**You can test this by running Docker’s equivalent of hello-world (without prefixing sudo):**

```
docker run hello-world
```

#### **Your node registration code**

First, goto your [Node's dashboard page](https://nodes.presearch.com/dashboard) and note down personal Node registration code. You will need this later to start the presearch-node container.\
****

![](https://lh5.googleusercontent.com/nNj2qzd6LYWJ1UzycUvtk6g8iFuFmFikQB1sgYYiBsZO1UfXcDNRAMA8Ht3gJxm74vVeoKiH3ddoCLZ7l8gSFsKvCtFvIKKdOQN63oqsYTVzikEKK9iUeXg\_H65uhBc7YCUkRv0b)

**Click on “Copy” to copy the code to your clipboard.**

## **Presearch Auto-updater**

Now, we install the presearch-node and an automatic updater. To ensure the presearch node always runs the latest image we are using the the Presearch Auto-updater image to check the presearch-node image every 900 seconds (15 minutes) for an updated version and if found, to automatically update it.\
****

```
docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --cleanup --interval 900 presearch-auto-updater presearch-node
```

## **Presearch node**

And finally, we download, and then start a presearch-node container. \


Execute the below in your terminal, making sure you replace \[YOUR\_REGISTRATION\_CODE] with the code you picked up from your node-control panel.

* \[NODE\_DESCRIPTION] with the descriptive name of your node

```
docker pull presearch/node

docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION_CODE=[YOUR_REGISTRATION_CODE] presearch/node
```

Since version 0.9.21, there are additional parameters you can enter at startup to pre-set some parameters for your node. These are:

* DESCRIPTION : this will be the descriptive text for your node,
* URL : to find out still, from the upcoming medium post ;-)
* STAKE : to stake an amount of PRE from node startup.

This would make the full command something like:\
****

```
docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION_CODE=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX -e DESCRIPTION="My Favorite Node" -e URL="https://my-hosting-provider.com/my-node-admin-page" -e STAKE=10000 presearch/node
```

#### Check if things are running properly by typing in the following command:

```
docker logs -f presearch-node
```

If all works as planned, you should see something like the below. You can get back to the command prompt by pressing CTRL+C.

![](https://lh4.googleusercontent.com/F5tGLw9SqQ7y8W5jrdj0N0wXoWAbcwvw8dLDFfCjH2\_Vv\_nk\_L8GsVSk\_RaBKtMY\_Vvq1zo3u2GEwXPq1qRVf32sYm4O-I4pm8HHX69GJUDO6Z1ouMEQqUA9ZU6GI9jKRSZEKsXf)

**Once back at the command prompt, type EXIT to close your terminal session.**

Thank you so much to our Presearch Community member Niels for putting this together for us.\
