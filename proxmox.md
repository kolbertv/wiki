#### Create VM from img from https://cloud-images.ubuntu.com/ (gui and Shell)

* Create VM from GUI
* VM - Hardware - Detach hard disk
* VM - Hardware - Remove unused disk
* Download img in a console of host machine
```
wget https://cloud-images.ubuntu.com/jammy/current/jammy-server-cloudimg-amd64.img
```
* Add img to VM
```
qm importdisk 1000 jammy-server-cloudimg-amd64.img local-lvm
```
* Set img as bootdisk
```
qm set 1000 --boot c --bootdisk scsi0
```
* VM - Hardware - Add unused disk
* VM - Hardware - Add - Cloudinit drive
* VM - Cloud-init - set User, Password, IP config
* VM - Cloud-init - Regenerate Image


#### Create VM from img from https://cloud-images.ubuntu.com/ (Shell of host machine)

* Download img in a console of host machine
```
wget https://cloud-images.ubuntu.com/jammy/current/jammy-server-cloudimg-amd64.img
```
* Create VM
```
qm create 1000 --memory 4096 --net0 virtio,bridge=vmbr0 --agent 1
```
* Import img
```
qm importdisk 1000 jammy-server-cloudimg-amd64.img local-lvm
```
* Atach disk
```
qm set 1000 --scsihw virtio-scsi-pci --scsi0 local-lvm:vm-1000-disk-0
```






