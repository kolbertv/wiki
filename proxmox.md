#### Create VM from img from https://cloud-images.ubuntu.com/

* Create VM from GUI
* VM - Hardware - Detach and Remove Disk
* Download img
```
wget https://cloud-images.ubuntu.com/jammy/current/jammy-server-cloudimg-amd64.img
```

```
qm importdisk 1000 jammy-server-cloudimg-amd64.img local-lvm
```


* VM - Hardware - Add - Cloudinit drive


