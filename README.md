# ks3

```
Biradars-MacBook-Air-4:~ sangam$ ssh pi@raspberrypi.local
pi@raspberrypi.local's password: 
Linux raspberrypi 4.19.42-v7+ #1219 SMP Tue May 14 21:20:58 BST 2019 armv7l

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Mon Jul 22 00:41:50 2019 from fe80::c56:c290:247b:90d5%wlan0
pi@raspberrypi:~ $ sudo -i
root@raspberrypi:~# echo "cgroup_enable=cpuset cgroup_memory=1 cgroup_enable=memory" >>/boot/cmdline.txt
root@raspberrypi:~# cat /boot/cmdline.txt
dwc_otg.lpm_enable=0 console=serial0,115200 console=tty1 root=PARTUUID=c93e37e6-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet splash plymouth.ignore-serial-consoles
cgroup_enable=cpuset cgroup_memory=1 cgroup_enable=memory
root@raspberrypi:~# 
```
