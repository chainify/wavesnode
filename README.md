# Waves Platform mainnet docker image

## Installation guide

### Create environment
Run remote server with Ubuntu 18
```
ssh root@YOUR_SERVER_IP
apt-get update
apt-get install -y docker.io
apt-get install -y docker-compose
```
Add required folders
```
cd /root
mkdir .waves && cd .waves
mkdir mainnet compose
```

### Pull this repository
Will download required docker images and configure nginx server
```
cd compose
git clone https://github.com/chainify/wavesnode.git .
```

### Update fullnode config file
```
cd fullnode
mv waves-fullnode.example.conf waves-fullnode.conf 
nano waves-fullnode.conf
```
All empty fields are required

### Pull docker images
Inside `/root/.waves/compose` directory run
```
docker-compose pull
docker-compose up -d
```

Follow blockchain node logs with
```
docker logs -f waves-fullnode --tail 200
```

