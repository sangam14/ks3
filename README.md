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
root@raspberrypi:~# k3s
NAME:
   k3s - Kubernetes, but small and simple

USAGE:
   k3s [global options] command [command options] [arguments...]

VERSION:
   v0.7.0 (61bdd852)

COMMANDS:
     server   Run management server
     agent    Run node agent
     kubectl  Run kubectl
     crictl   Run crictl
     ctr      Run ctr
     help, h  Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --debug        Turn on debug logs
   --help, -h     show help
   --version, -v  print the version
root@raspberrypi:~# k3s kubectl get nodes
NAME          STATUS   ROLES    AGE     VERSION
raspberrypi   Ready    master   3h28m   v1.14.4-k3s.1
root@raspberrypi:~# k3s kubectl get po,svc,deploy
NAME                           READY   STATUS    RESTARTS   AGE
pod/mynginx-74bc69fc95-jv9tl   1/1     Running   0          3h22m
pod/mynginx-74bc69fc95-rwk9z   1/1     Running   0          3h22m
pod/mynginx-74bc69fc95-tv4kl   1/1     Running   0          3h22m

NAME                 TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.43.0.1       <none>        443/TCP   3h29m
service/mynginx      ClusterIP   10.43.152.228   <none>        80/TCP    3h21m

NAME                            READY   UP-TO-DATE   AVAILABLE   AGE
deployment.extensions/mynginx   3/3     3            3           3h22m
root@raspberrypi:~# k3s kubectl get endpoints mynginx
NAME      ENDPOINTS                                  AGE
mynginx   10.42.0.10:80,10.42.0.11:80,10.42.0.9:80   3h21m
root@raspberrypi:~# curl 10.42.0.10:80
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
root@raspberrypi:~# 





```
