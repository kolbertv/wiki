#### add img from https://cloud-images.ubuntu.com/

* Create VM from GUI

```
wget https://cloud-images.ubuntu.com/jammy/current/jammy-server-cloudimg-amd64.img
```

```
qm importdisk 1000 jammy-server-cloudimg-amd64.img local-lvm
```
