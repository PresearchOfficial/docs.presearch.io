---
description: How to get you AWS server up & running
---

# Running a Node on AWS

{% embed url="https://youtu.be/E8krsTCTgjs" %}



## Steps

1. Create an AWS Account. This will take just a few minutes.
2. Create an instance
3. Select one of the Ubuntu (i used the first one)
4. launch your instance, save your private keys in a separate folder
5. Open terminal, copy & paste the codes from AWS. It should look like this

```bash
ssh -i "yourPrivateKey.pem" ubuntu@ec2-18-221-247-250.us-east-2.compute.amazonaws.com
```

6\. You should then be connected to your AWS instance - all you need to do now is install docker with these commands

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
```

```bash
sudo sh get-docker.sh
```

7\. you then need to set up an auto updater for your node with this command in the term

```bash
sudo docker run -d --name presearch-auto-updater --restart=unless-stopped -v /var/run/docker.sock:/var/run/docker.sock presearch/auto-updater --cleanup --interval 900 presearch-auto-updater presearch-node
```

8\. Then, pull the node & run it with these commands (make sure to replace YourRegistrationCodeHere in the second piece of code with your registration code from your account)

```bash
sudo docker pull presearch/node
```

```bash
sudo docker run -dt --name presearch-node --restart=unless-stopped -v presearch-node-storage:/app/node -e REGISTRATION_CODE=YourRegistrationCodeHere presearch/node
```

9\. You can then run this to see if your node is working (: You should see the PRE logo.

```bash
sudo docker logs -f presearch-node
```

10\. finally, you can exit out of the terminal & go into your [dashboard](https://nodes.presearch.org/dashboard) to see the node, name it & stake your coins on it!

{% hint style="info" %}
if you have any questions, make sure to ask it in the [nodes telegram channel](https://t.me/PresearchNodes)
{% endhint %}
