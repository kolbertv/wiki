#### Tunnel from VPS to local pc
##### Server side (VPS)

```
[Interface]
Address = 10.200.10.1/32
PrivateKey = server-private-key
ListenPort = 52820

[Peer]
PublicKey = client-public-key
AllowedIPs = 10.200.10.2/32
PersistentKeepalive = 25
```
##### Client side(local pc)

```
[Interface]
Address = 10.200.10.2/32
PrivateKey = client-private-key

[Peer]
PublicKey = server-public-key
AllowedIPs = 10.200.10.1/32
Endpoint = 80.80.80.81:52820
PersistentKeepalive = 25
```
