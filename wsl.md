#### Update date and time in ubuntu
```
sudo ntpdate pool.ntp.org
```

#### Reduce size of vdisk of wsl (windows and diskpart)

##### To find where stored vdisk
```
 C:\Users\<User name>\AppData\Local\Packages\<distr name>\LocalState\ext4.vhdx
```

##### windows power shell (run diskpart)
```
diskpart
```

##### Select vdisk
```
select vdisk file="C:\Users\<User name>\AppData\Local\Packages\<distr name?\LocalState\ext4.vhdx"
```

##### Details of disk
```
 detail vdisk
```

##### Compact disk
```
 compact vdisk
```
