#### Welcome screen for SSH add IP
##### Create file
```
nano /etc/update-motd.d/01-custom
```

##### Add
```
#!/bin/sh
ip a | grep "inet" 
```

##### Then
```
chmod +x /etc/update-motd.d/01-custom
reboot
```
