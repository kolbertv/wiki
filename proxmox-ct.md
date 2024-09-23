#### Config container
##### Create container (Ubuntu)
##### Back to the host
Edit the config file for the container (/etc/pve/lxc/$ID.conf) and add the following:

```
lxc.apparmor.profile: unconfined
lxc.cgroup.devices.allow: a
lxc.cap.drop:
lxc.mount.auto: "proc:rw sys:rw"
```
##### In the container
/etc/rc.local doesn't exist in the default 20.04 LXC template provided by Proxmox. Create it with these contents:
```
#!/bin/sh -e

# Kubeadm 1.15 needs /dev/kmsg to be there, but it's not in lxc, but we can just use /dev/console instead
# see: https://github.com/kubernetes-sigs/kind/issues/662
if [ ! -e /dev/kmsg ]; then
    ln -s /dev/console /dev/kmsg
fi

# https://medium.com/@kvaps/run-kubernetes-in-lxc-container-f04aa94b6c9c
mount --make-rshared /
```

##### Then run:
```
chmod +x /etc/rc.local
reboot
```



----------------
#### Add SSH to proxmox container(LXC)
##### Root password
```
passwd root
```

##### Enable ssh
edit file
```
nano /etc/ssh/sshd_config
```
 change to
```
PermitRootLogin yes
```

##### Restart SSH
```
systemctl restart sshd
```
