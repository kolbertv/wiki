
##### install master
```
curl -fsL https://get.k3s.io | sh -s - --disable traefik --node-name control.k8s
```

##### get token 
```
cat /var/lib/rancher/k3s/server/node-token
```
##### create node
```
curl -sfL https://get.k3s.io | K3S_URL=https://myserver:6443 K3S_TOKEN=mynodetoken sh -

```
