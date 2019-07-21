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

root@raspberrypi:~#  curl -sfL https://get.k3s.io | sh -
[INFO]  Finding latest release
[INFO]  Using v0.7.0 as release
[INFO]  Downloading hash https://github.com/rancher/k3s/releases/download/v0.7.0/sha256sum-arm.txt
[INFO]  Downloading binary https://github.com/rancher/k3s/releases/download/v0.7.0/k3s-armhf
[INFO]  Verifying binary download
[INFO]  Installing k3s to /usr/local/bin/k3s
[INFO]  Creating /usr/local/bin/kubectl symlink to k3s
[INFO]  Creating /usr/local/bin/crictl symlink to k3s
[INFO]  Creating killall script /usr/local/bin/k3s-killall.sh
[INFO]  Creating uninstall script /usr/local/bin/k3s-uninstall.sh
[INFO]  env: Creating environment file /etc/systemd/system/k3s.service.env
[INFO]  systemd: Creating service file /etc/systemd/system/k3s.service
[INFO]  systemd: Enabling k3s unit
Created symlink /etc/systemd/system/multi-user.target.wants/k3s.service → /etc/systemd/system/k3s.service.
[INFO]  systemd: Starting k3s
root@raspberrypi:~# 
root@raspberrypi:~# sudo k3s kubectl get node -o wide
NAME          STATUS   ROLES    AGE     VERSION         INTERNAL-IP    EXTERNAL-IP   OS-IMAGE                         KERNEL-VERSION   CONTAINER-RUNTIME
raspberrypi   Ready    master   2m13s   v1.14.4-k3s.1   192.168.2.18   <none>        Raspbian GNU/Linux 9 (stretch)   4.19.42-v7+      containerd://1.2.7-k3s1
root@raspberrypi:~# 


```
