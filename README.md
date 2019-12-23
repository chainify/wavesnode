# Waves Platform mainnet docker image

## Installation guide
Based on [official wavesplatform documentation](https://docs.wavesplatform.com).

### Create environment
Run remote server with Ubuntu 18. Make sure to have at least 60Gb of storage.
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

### Pull docker images
Inside `/root/.waves/compose` directory run.
```
docker-compose pull
docker-compose up -d
```

### Display fullnode logs
```
docker logs -f waves-fullnode --tail 200
```

----
MIT license