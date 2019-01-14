---
layout: post
title: "Wireless CTF Notes using a Raspberry Pi"
tags:
  - code
modified: 2019-01-13
---

For WCTF it's a good idea to use Pentoo. However on short notice, I could only find Kali for Rapsberry Pi for an easy on-the-go build. Some notes for myself which might be useful to whoever reads this.

# Bluetooth Fox Hunting

First enable bluetooth:
```bash
systemctl enable bluetooth 
systemctl enable hciuart
```

For bluetooth fox-hunting:
* [blue_hydra](https://github.com/ZeroChaos-/blue_hydra)
* [ble_finder](https://github.com/hackerwarehouse/ble_finder/blob/master/ble_finder.py)
* [blue_sonar](https://github.com/ZeroChaos-/blue_sonar)

For finding bluetooth with ble_finder, edit `blue_hydra.yml` to set:
```bash
rssi_log: true
```
Then use ble_finder to locate the devices in the list specified in the python script.

Alternatively, use blue_sonar to find the MAC you are hunting:
```bash
blue_sonar -t XX:XX:XX:XX:XX:XX
```

# Bluetooth spoofing

To change/spoof the bluetooth MAC address on Raspberry Pi, you'll need the tool bdaddr[^1]:
```bash
apt-get install libbluetooth-dev
wget -U firefox https://drive.google.com/open?id=1Gu4SSI8Rem3iFcCT70dRHKB4UGdee7n_
bzip2 -d bdaddrtar.bz2 && tar xf bdaddrtar
cd bdaddr && make
```
First confirm your original MAC address
```bash
$ hcitool dev
Devices:
        hci0    AA:AA:AA:AA:AA:AA
```
Run `bdaddr` to change the address:
```bash
$ ./bdaddr -i hci0 -r 00:11:22:33:44:55
Manufacturer:   Broadcom Corporation (15)
Device address: AA:AA:AA:AA:AA:AA
New BD address: 00:11:22:33:44:55

Address changed - Device reset successully
```
Reset and restart the hci device and bluetooth service
```bash
hciconfig hci0 reset
systemctl restart bluetooth.service
```
Finally, doublecheck the change:
```bash
$ hcitool dev
Devices:
        hci0    00:11:22:33:44:55
```

# Wifi spoofing
To spoof wifi MAC address, download `macchanger`
```bash
apt-get install macchanger
macchanger -h
macchanger -m XX:XX:XX:XX:XX:XX
```


<br>
Sources:

[^1]: [https://scribles.net/changing-a-bluetooth-device-address-on-raspberry-pi/](https://scribles.net/changing-a-bluetooth-device-address-on-raspberry-pi/)