#### Reverse proxy (config for wireguard https://github.com/kolbertv/wiki/blob/master/wireguard.md)
##### VPS side ()

```
user www-data;
worker_processes auto;
pid /run/nginx.pid;
include /etc/nginx/modules-enabled/*.conf;

events {
        worker_connections 768;
        # multi_accept on;
}

stream {
        server {
                listen 80.80.80.81:80;
                proxy_pass 10.200.10.2:80;
                proxy_protocol on;
        }
        server {
                listen 80.80.80.81:443;
                proxy_pass 10.200.10.2:443;
                proxy_protocol on;
        }
}

```

##### Some example for local pc
```
http {
    server {
        listen 80 proxy_protocol;
        server_name *.somesite1.io;

        location / {
            proxy_pass http://192.168.0.10:80
        }
    }
    server {
        listen 80 proxy_protocol;
        server_name *.somesite2.io;

        location / {
            proxy_pass http://192.168.0.11:80
        }
    }
    server {
        listen 80 proxy_protocol;
        server_name 80.80.80.81;
        return 444
    }
}
```

#### k3s
##### install and deploy
```
kubectl create deploy nginx --image nginx:latest
```

##### expose nginx
```
kubectl expose deploy nginx --port=80 --type=LoadBalancer
```
