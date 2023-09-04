---
description: Here is a quick guide to launching your PreSearch Node on StackOS.
---

# Running a node on Stack OS

We assume you already have your PreSearch Node Registration Code and account set up.  If you need more details on that reference this: [https://docs.presearch.org/nodes/setup](https://docs.presearch.org/nodes/setup)\
\
Go to your [Node's dashboard](https://nodes.presearch.com/dashboard) and have your Presearch Node Registration Code ready.

## Fund your StackOS Account:

Go to [https://app.stackos.io/](https://app.stackos.io/) and login with Metamask

* BSC MainNet
* Choose Cluster:
  * Dev/Test: Titan or Matrix Cluster
  * Production: Authority for high uptime deploys

Go to the upgrade tab:

![](<../../.gitbook/assets/stackos presearch upgrade menu.png>)\
Type in the following information

![](<../../.gitbook/assets/stackos presearch upgrade package.png>)\
As a note, we can assign the resources as follows:  &#x20;

* CPU as follows: 2000 for PreSearch, 100 for webtty  &#x20;
* RAM: 4000 for PreSearch, 100 for webtty &#x20;
* Disk: 16-32 GB for PreSearch\
  \
  You will be given a quote for the number of $STACK tokens you need to deposit.\
  Buy some $STACK tokens from Pancake Swap and deposit that amount into StackOS[https://medium.com/stackos/how-to-buy-stack-on-pancakeswap-using-metamask-3e122dc04061](https://medium.com/stackos/how-to-buy-stack-on-pancakeswap-using-metamask-3e122dc04061)\
  \
  Click the Deposit or Upgrade button to fund your StackOS account![](<../../.gitbook/assets/Screen Shot 2022-01-10 at 11.41.51 AM.png>)



## Go to the AppStore

![
](<../../.gitbook/assets/image (8).png>)

## Launch your PreSearch Node



![](<../../.gitbook/assets/image (1) (1).png>)

![](<../../.gitbook/assets/image (2) (1).png>)

![](<../../.gitbook/assets/Screen Shot 2022-01-11 at 4.16.57 AM.png>)

## Verify Operation

\
Check [https://nodes.presearch.com/dashboard](https://nodes.presearch.com/dashboard) and verify your node appears on the list

![](<../../.gitbook/assets/image (4).png>)

Look for green connection icon

![](<../../.gitbook/assets/image (5) (1).png>)

## Troubleshooting

\
If your node is not starting properly for some reason, consider opening a WebTTY and checking the logs:\
\
Create a WebTTY [StackOS - WebTTY (external)](https://www.evernote.com/shard/s79/sh/647ab636-068b-946f-9cf5-2c6e9895c0a9/43124974ed3a91d7f41cc255325aba7b)

### Get the name of the presearch-0x... pod

\
kubectl get pods\
\


### Show the logs for the pod

`kubectl logs -f presearch-0xYOURETHADDRESS-RANDOM`\


### Expect to see something like this

![](<../../.gitbook/assets/image (6).png>)
