
##### Install and deploy metalllab
```
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.14.5/config/manifests/metallb-native.yaml
```

##### Check namespace metallb-system
```
kubectl get namespaces
```

##### Check pods
```
kubectl get pods -n metallb-system
```


##### config metalllab

```
nano metallb.yaml

apiVersion: metallb.io/v1beta1
kind: IPAddressPool
metadata:
  name: production
  namespace: metallb-system
spec:
  addresses:
  - 192.168.1.30-192.168.1.50
---
apiVersion: metallb.io/v1beta1
kind: L2Advertisement
metadata:
  name: l2-advert
  namespace: metallb-system

```
