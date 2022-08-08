---
description: Setup a node at home less than $100.
---

# Setup Nodes on Raspberry Pi

## Overview

Running a node on a Raspberry Pi enables people from all over the world to operate a Presearch node that runs 24/7 from your house for $50 - $100. If you’re unfamiliar with what Raspberry Pi is (no, it’s not a kind of pie your grandma makes) it’s a cheap computer that can run a node on low energy and makes it easier to run a Presearch node really cheaply.

## Hardware Requirements <a href="#f4ad" id="f4ad"></a>

### Minimum Requirements

1. A [Raspberry Pi](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/) with [Power Adapter](https://www.amazon.com/CanaKit-Raspberry-Power-Supply-PiSwitch/dp/B07TSFYXBC).
2. A [Micro SD card](https://www.newegg.com/team-32gb-microsdhc/p/20-313-309) (16GB will be fine for now, though you may eventually want more capacity or an external hard drive to support future node operations).
3. **Recommended**: An ethernet cable to directly plug into the internet instead of using WiFi (this will improve your node's reliability).

### Needed for Initial Setup

1. Another computer (Max/Windows/Ubuntu) with an internal or external MicroSD card reader&#x20;
2. A USB mouse and keyboard to walk through the setup process
3. An external monitor or TV to see the output from your Raspberry Pi during setup
4. Micro HDMI cable to connect your Raspberry PI to an external monitor or TV

**Note**: If this is your first time setting up a Raspberry Pi, you might consider purchasing a [starter kit](https://www.canakit.com/raspberry-pi/pi-4-kits) which contains all of the necessary accessories.&#x20;

## Operating System Setup

In order to run a Presearch Node on the Raspberry Pi, you'll first need to install the Raspberry Pi 64 Bit Operating System as follows:

On your main computer (not your Raspberry Pi):

1. Download the latest [64 Bit Raspberry PI Operating System](https://downloads.raspberrypi.org/raspios\_arm64/images/raspios\_arm64-2021-05-28/2021-05-07-raspios-buster-arm64.zip) image
2. Insert your SD card into your MicroSD card reader
3. Download the Raspberry Pi Image Tool from [here](https://www.raspberrypi.com/software/) and run it

#### 1. Click "Choose OS"

![](<../.gitbook/assets/Screen Shot 2021-08-26 at 11.29.08 AM.png>)

#### 2. In the drop-down list, select the "Use custom" image option

![](<../.gitbook/assets/Screen Shot 2021-08-26 at 11.29.58 AM.png>)

#### 3. Find and select the `2021–05–07-raspios-buster-arm64.zip` image you downloaded.

![](<../.gitbook/assets/Screen Shot 2021-08-26 at 11.31.10 AM.png>)

#### 4. Click the "Choose Storage" Button

![](<../.gitbook/assets/Screen Shot 2021-08-27 at 11.17.58 AM.png>)

#### 5. Select the plugged in MicroSD Card

![](<../.gitbook/assets/Screen Shot 2021-08-26 at 11.34.27 AM.png>)

#### 6. Click the "WRITE" button

![](<../.gitbook/assets/Screen Shot 2021-08-26 at 11.34.55 AM.png>)

#### 7. Confirm that you understand all data on the MicroSD card will be erased:

![](<../.gitbook/assets/Screen Shot 2021-08-26 at 11.35.18 AM.png>)

#### 7. Wait for the operating system image to finish writing

![](<../.gitbook/assets/Screen Shot 2021-08-26 at 11.35.46 AM.png>)

![](<../.gitbook/assets/Screen Shot 2021-08-26 at 11.53.11 AM.png>)

#### 9. Take the microSD card out of your main computer, insert it into your Raspberry Pi, and power on your Raspberry Pi.

**Note**: You will need to connect you Raspberry PI to a monitor and plug in your mouse and keyboard to the Raspberry Pi to complete the remaining setup. We also STRONGLY recommend using an ethernet cable to connect you Raspberry Pi to the internet instead of WiFi, as your node's reliability score (which affect how often it is used and rewards earned) will be lower over WiFi.

#### 10. When the Raspberry Pi boots for the first time, follow the instructions in the Setup Wizard to configure your system settings:&#x20;

![](<../.gitbook/assets/image (8).png>)

You'll configure to following settings based upon your own needs:\
• Country, Language, Timezone, Keyboard\
• Password\
• Screen Settings\
• Wifi (optional)\


#### 11. When you get to the Software Update screen, be sure to click "Next" to update your system.&#x20;

Do **NOT** skip the software updates, as it could expose your system to security issues or prevent your node from installing correctly.\


![](<../.gitbook/assets/image (14).png>)



#### 12. On the final "Setup Complete" Screen, click "Restart".

![](<../.gitbook/assets/image (9).png>)

Once your successfully system restarts, you'll be ready to install Docker and start your node!

## Install Docker

To install Docker on your Raspberry Pi, perform the following steps

#### 1. Click the Terminal icon in the system menu bar to open a terminal

![](<../.gitbook/assets/image (12).png>)

#### 2. Run the following command to download and install Docker

```bash
curl -sSL https://get.docker.com | sh
```

#### 3. Add your user to the "docker" permissions group

```bash
sudo usermod -aG docker $USER && newgrp docker
```

Congratulations - Docker is now successfully installed and your system is ready to install and run the Presearch Node!

## Install the Presearch Node

The last step is to install your Presearch Node, which only requires running one more command! Follow the [**Node Setup Instructions** ](setup.md) to run the final command to get your node up and running!
