
##### install master
```
curl -fsL https://get.k3s.io | sh -s - --disable traefik --node-name control.k8s
```

##### get token 
```
cat /var/lib/rancher/k3s/server/node-token
```
