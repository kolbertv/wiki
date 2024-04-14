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
                proxy_pass 10.200.1.2:80;
                proxy_protocol on;
        }
        server {
                listen 80.80.80.81:443;
                proxy_pass 10.200.1.2:443;
                proxy_protocol on;
        }
}

```
