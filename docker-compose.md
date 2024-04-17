#### Portainer

docker-compose.yml
```
version: "3"
services:
  portainer:
    image: portainer/portainer-ce:latest
    ports:
      - 9443:9443
    volumes:
      - data:/data
      - /var/run/docker.sock:/var/run/docker.sock
    restart: unless-stopped
volumes:
  data:
```

#### Mongo db
```
services:
  mongo1:
    image: mongo
    hostname: mongo1
    container_name: mongo1
    ports:
      - '27017:27017'
    volumes:
      - ./mongorestore.sh:/docker-entrypoint-initdb.d/mongorestore.sh
      - ./markdb:/markdb
    # entrypoint: > 
    #   /usr/bin/mongod --bind_ip_all --replSet rs0;
    restart: always

  # mongo-init-replica:
  #   image: mongo
  #   depends_on:
  #     - mongo1   
  #   volumes:
  #     - ./deployment_scripts:/deployment_scripts
  #   entrypoint:
  #     - /deployment_scripts/initiate_replica.sh

```
mongorestore.sh
```
mongorestore -d markdb  /markdb
```
initiate_replica.sh
```
#!/bin/bash
  
echo "Starting replica set initialize"
until mongosh --host mongo1 --eval "print(\"waited for connection\")"
do
    sleep 2
done
echo "Connection finished"
echo "Creating replica set"
mongosh --host mongo1 <<EOF
rs.initiate(
  {
    _id : 'rs0',
    members: [
      { _id : 0, host : "mongo1:27017" },
    ]
  }
)
EOF
echo "replica set created"
```
