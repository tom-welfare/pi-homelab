# pi-homelab

Official documentation for the Raspberry Pi can be found [here](https://www.raspberrypi.org/documentation/).

## Getting started

Insert the microSD card, connect a USB keyboard and mouse, plug in an HDMI cable, ethernet cable and the micro-USB power supply.

Go through the setup wizard from the microSD card and install Raspberry Full OS (32 bit).

If you didn't change the password during the setup wizard, open a terminal and do so now by running:

```bash
passwd pi
```

### Enabling remote access

Once the initial setup has completed, we need to enable remote access to your Pi. In the top-right corner of the UI, connect to your wireless network.

Once the connect to the wireless network has succeeded, you can disconnect the ethernet cable, we won't need this any further.

First, you will need to enable ssh on your PI:

```bash
sudo systemctl enable ssh
sudo systemctl start ssh
```

Then obtain the IP address of the Pi on the network:

```bash
hostname -I
```

In Google Home Wifi, set this as a static IP address for your Pi, so that we can always connect to this machine on the same IP.

**On your laptop**, add this ip address to your hosts file:

```bash
PI_NAME=<add pi name here>
PI_IP=<ip address>
sudo echo  "${PI_IP}  ${PI_NAME}" >> /etc/hosts
```

You should now be able to connect to the Pi from your laptop, entering your password when prompted:

```bash
ssh pi@${PI_NAME}
```

To enable keyless ssh, add your key to the Pi:

```bash
ssh-copy-id pi@${PI_NAME}
```

You should now be able to access your Pi via SSH on your laptop now, so we can disconnect the HDMI cable, along with the USB keyboard and mouse.

### Updating the system configuration

To edit system configuration for the Pi, we can run the `raspi-config` utility using:

```bash
sudo raspi-config
```

We should update the following settings:

- hostname
- enable VNC
- ...

### Todo

Install vim

```bash
sudo apt-get update
sudo apt-get install vim
```

Install zsh and ohmyzsh, vim config, ...
