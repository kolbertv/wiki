##### minimal example

```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: test-nginx
spec:
  ingressClassName: nginx 
  rules:
  - host: exampl.exampl.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: example-svc
            port:
              number: 80

```
