##### export config
```
export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
```

##### add repo for dashboard
```
helm repo add kubernetes-dashboard https://kubernetes.github.io/dashboard/
```

##### install dashboard by helm
```
helm upgrade --install kubernetes-dashboard kubernetes-dashboard/kubernetes-dashboard --create-namespace --namespace kubernetes-dashboard --set 'api.containers.args={--disable-csrf-protection=true}' --set kong.proxy.http.enabled=true
```

##### add account
```
---
apiVersion: v1
kind: ServiceAccount
metadata:
  name: admin-user
  namespace: kubernetes-dashboard

---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: admin-user
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
- kind: ServiceAccount
  name: admin-user
  namespace: kubernetes-dashboard
```




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

#### If you has termination for ssl before (nginx proxy)
##### Enable http and disable csrf
```
helm upgrade --install kubernetes-dashboard kubernetes-dashboard/kubernetes-dashboard --create-namespace --namespace kubernetes-dashboard --set 'api.containers.args={--disable-csrf-protection=true}' --set kong.proxy.http.enabled=true
```

##### Ingress file for dashboard
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  namespace: kubernetes-dashboard
  name: kubernetes-dashboard-ingress
spec:
  ingressClassName: nginx
  rules:
  - host: dashboard.example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: kubernetes-dashboard-kong-proxy
            port:
              number: 80
```
