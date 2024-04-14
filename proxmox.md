#### Create VM from img from https://cloud-images.ubuntu.com/

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
