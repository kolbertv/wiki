
#### Proxy dashboard from master node to localhost
##### Proxy from master node
```
kubectl -n kubernetes-dashboard port-forward svc/kubernetes-dashboard-kong-proxy 8443:443
```
##### Tunel by SSH
```
ssh -N -L 8001:127.0.0.1:8443 root@192.168.1.100
```
##### URL to dashboard
```
https://localhost:8001
```

##### Create token
```
kubectl -n kubernetes-dashboard create token USER_BAME
```
