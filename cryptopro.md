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

#### Delete license(windows)
start regedit.

delete:
```
HKEY_CLASSES_ROOT\WOW6432Node\CLSID\{4BE57065-DC50-4239-8E32-11FABAF5ECF5}
```
```
HKEY_CLASSES_ROOT\WOW6432Node\CLSID\{C8B655BB-28A0-4BB6-BDE1-D0826457B2DF}
```

reisntall CryptoPro
