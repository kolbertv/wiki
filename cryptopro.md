#### Install cyrpto pro
```
 wget https://cryptopro.ru/sites/default/files/private/csp/50/12999rc4/linux-amd64_deb.tgz
```
```
 tar -xvf linux-amd64_deb.tgz
```
```
sudo ./install.sh
```

#### Uninstall crypto pro

Delete cryptopro
```
cd ~/linux-amd64_deb
sudo ./uninstall.sh
```
delete licence
```
sudo rm -rf /etc/opt/cprocsp
```
delete certificate
```
sudo rm -rf /var/opt/cprocsp
```
