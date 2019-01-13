---
layout: post
title: "Kali Linux on Raspberry Pi"
tags:
  - code
modified: 2019-01-12
---

Just some notes on my Kali build with Raspberry Pi...

# 0. Materials:
* [Raspberry Pi 3 B+](https://amzn.to/2sjZMse)
* [Adafruit PiTFT 2.2" HAT Part #2315](https://amzn.to/2sqKKRy)
* [MicroSD Card w/ USB](https://amzn.to/2CkUnWr)
* [Kali Linux ARM Image](https://www.offensive-security.com/kali-linux-arm-images/)

Soldering is required to attach the header that connects the hat to the pi.

# 1. Prepare OS
Download the image and use [Etcher](https://www.balena.io/etcher/) to flash the SD card with Kali Linux. You don't even have to decompress the image.

# 2. Basic Setup
Insert the SD card into the Raspberry Pi and plug in the micro USB power source.

You'll need to hook up an external monitor for the first boot in order to prepare the machine for console use.

Login as `root:toor`, set up the wifi, and run the standard stuff:
```bash
apt-get update
apt-get full-upgrade
```
Make sure to change the default password:
```bash
passwd root
```
Change the default SSH keys:
```bash
dpkg-reconfigure openssh-server
```
Edit the file `/etc/ssh/sshd_config` and change the line with `PermitRootLogin` to:
```bash
PermitRootLogin yes
```
Finally, enable autologin so that ssh can work on boot[^1][^2]. Edit `/etc/lightdm/lightdm.conf` and uncomment the lines:
```bash
autologin-user=root
autologin-user-timeout=0
```
Next edit `/etc/pam.d/lightdm-autologin` and comment out:
```bash
# auth required pam_succeed_if.so user != root quiet_success
```
After this step, you can reboot whenever and have ssh access with your root user.

# 3. Prepare for a console-only experience
Set Kali to boot into console mode:
```bash
systemctl set-default multi-user.target
systemctl get-default # this command checks the setting
reboot
```
Clone the following repos:
* [https://github.com/adafruit/Raspberry-Pi-Installer-Scripts.git](https://github.com/adafruit/Raspberry-Pi-Installer-Scripts.git)
* [https://github.com/doceme/py-spidev.git](https://github.com/doceme/py-spidev.git)

The first repo has `adafruit-pitft.sh` which is used to automatically configure the TFT display but since we're on Kali some of the dependencies for the script are unvailable which is why we need the second repo.

In the `py-spidev` folder, run:
```bash
make
make install
```

Go into the `Raspberry-Pi-Installer-Scripts` folder and edit the `adafruit-pitft.sh` file. In this file, remove the part where it tries to install `python-spidev` and `tslib`. Then, run:
```bash
./adafruit-pitft.sh -u /root
```
This will ask you what screen you have and what configuration/rotation you prefer.
Afterwards, when you reboot you should see the console show up on the display. I prefer the `270 degrees (landscape)` setting as this will place the buttons below the display.

I'm still unable to figure out the buttons on a Kali image. If anyone out there has any input, please let me know :)



<br>
Sources:

[^1]: [https://null-byte.wonderhowto.com/how-to/set-up-headless-raspberry-pi-hacking-platform-running-kali-linux-0176182/](https://null-byte.wonderhowto.com/how-to/set-up-headless-raspberry-pi-hacking-platform-running-kali-linux-0176182/)
[^2]: [https://null-byte.wonderhowto.com/how-to/set-up-kali-linux-new-10-raspberry-pi-zero-w-0176819/](https://null-byte.wonderhowto.com/how-to/set-up-kali-linux-new-10-raspberry-pi-zero-w-0176819/)