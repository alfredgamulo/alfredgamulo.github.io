---
layout: post
title: "Expanding an AWS Linux Partition"
description: "Simple copy paste of steps to increase the AWS linux partition after enlarging the volume."
tags: 
  - code
modified: 2015-06-18
---

A couple of days ago, I went through the steps of enlarging my AWS instance volume as well as switching over from magnetic drives to SSD. I thought everything would just work magically when I restarted the instance but instead found that the file system did not recognize the change in disk size. I should not have assumed that the VM would know how I want to use the extra disk space.

The following shell output details the steps required to expand the Linux file system after increasing the instance volume size.

{% highlight Bash shell scripts %}

[ec2-user@service ~]$ df -h # check the filesystem
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup-lv_root
                       14G  5.6G  8.4G  40% /
tmpfs                 3.6G     0  3.6G   0% /dev/shm
/dev/xvda1            485M   54M  407M  12% /boot

[ec2-user@service ~]$ lsblk # observe how the disk, partition, and lvm is laid out
NAME                        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
xvda                        202:0    0   30G  0 disk 
├─xvda1                     202:1    0  500M  0 part /boot
└─xvda2                     202:2    0 15.5G  0 part 
  ├─VolGroup-lv_root (dm-0) 253:0    0 13.9G  0 lvm  /
  └─VolGroup-lv_swap (dm-1) 253:1    0  1.6G  0 lvm  [SWAP]

[ec2-user@service ~]$ sudo parted /dev/xvda # use parted to expand the second partition
GNU Parted 2.1
Using /dev/xvda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) print                                                            
Model: Xen Virtual Block Device (xvd)
Disk /dev/xvda: 62914560s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start     End        Size       Type     File system  Flags
 1      2048s     1026047s   1024000s   primary  ext4         boot
 2      1026048s  33554431s  32528384s  primary               lvm

(parted) rm 2                                                             
Warning: WARNING: the kernel failed to re-read the partition table on /dev/xvda (Device or resource busy).  As a result, it may not
reflect all of your changes until after reboot.
(parted) mkpart primary 1026048s 100%                                     
Warning: WARNING: the kernel failed to re-read the partition table on /dev/xvda (Device or resource busy).  As a result, it may not
reflect all of your changes until after reboot.
(parted) print                                                            
Model: Xen Virtual Block Device (xvd)
Disk /dev/xvda: 62914560s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start     End        Size       Type     File system  Flags
 1      2048s     1026047s   1024000s   primary  ext4         boot
 2      1026048s  62914559s  61888512s  primary

(parted) quit                                                             
Information: You may need to update /etc/fstab.                           

[ec2-user@service ~]$ lsblk # observe that no changes until reboot
NAME                        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
xvda                        202:0    0   30G  0 disk 
├─xvda1                     202:1    0  500M  0 part /boot
└─xvda2                     202:2    0 15.5G  0 part 
  ├─VolGroup-lv_root (dm-0) 253:0    0 13.9G  0 lvm  /
  └─VolGroup-lv_swap (dm-1) 253:1    0  1.6G  0 lvm  [SWAP]

[ec2-user@service ~]$ sudo reboot now

[ec2-user@service ~]$ sudo pvresize /dev/xvda2 # resize the physical volume to occupy the full partition

[ec2-user@service ~]$ sudo lvextend /dev/mapper/VolGroup-lv_root /dev/xvda2 # resize the logical volume to occupy the full physical volume

[ec2-user@service ~]$ sudo resize2fs /dev/mapper/VolGroup-lv_root # resize the file system to occupy the full logical volume

[ec2-user@service ~]$ lsblk # observe that the lvm resize has taken place
NAME                        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
xvda                        202:0    0   30G  0 disk 
├─xvda1                     202:1    0  500M  0 part /boot
└─xvda2                     202:2    0 29.5G  0 part 
  ├─VolGroup-lv_root (dm-0) 253:0    0 27.9G  0 lvm  /
  └─VolGroup-lv_swap (dm-1) 253:1    0  1.6G  0 lvm  [SWAP]

[ec2-user@service ~]$ df -h # confirm that the file system has the new disk availability
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup-lv_root
                       28G  5.6G   21G  22% /
tmpfs                 7.3G     0  7.3G   0% /dev/shm
/dev/xvda1            485M   54M  407M  12% /boot

{% endhighlight %}
