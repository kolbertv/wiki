#### Welcome screen for SSH add IP
##### Create file
```
nano /etc/update-motd.d/01-custom
```

##### Add
```
#!/bin/sh

SIZE=$(df -h / | grep / | awk '{ print $2}')
USED=$(df -h / | grep / | awk '{ print $3}')
AVAIL=$(df -h / | grep / | awk '{ print $4}')
RAMSIZE=$(free -m | grep Mem | awk '{print $2}')
RAMUSED=$(free -m | grep Mem | awk '{print $3}')
RAMAVAIL=$(free -m | grep Mem | awk '{print $4}')

echo ""
echo "============================================="
echo ""
echo " - Hostname: `hostname -f`"
echo " - IP Address: `hostname --all-ip-addresses`"
echo " - SSD Size: $SIZE"
echo " - SSD Used: $USED"
echo " - SSD Available: $AVAIL"
echo ""
echo " - RAM Size: $RAMSIZE`+`M"
echo " - RAM Used: $RAMUSED`+`M"
echo " - RAM Available: $RAMAVAIL`+`M"
echo ""
echo "============================================="
echo ""
echo ""
echo ""
echo ""
```

##### Then
```
chmod +x /etc/update-motd.d/01-custom
reboot
```
