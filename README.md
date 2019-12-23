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

### Config envirinment varriables
- WAVES_NETWORK=mainnet
- WAVES_VERSION=latest
- BRANCH=version-0.17.x
- SBT_VERSION=1.2.8
- WAVES_LOG_LEVEL=DEBUG
- WAVES_HEAP_SIZE=2g
- WAVES__REST_API__ENABLE=yes
- WAVES__REST_API__BIND_ADDRESS=0.0.0.0
- WAVES__REST_API__PORT=6869

#### By default these variables are not provided. Uncomment them to pass to environment.
- WAVES_WALLET_SEED=
- WAVES_WALLET_SEED_BASE58=
- WAVES_WALLET_PASSWORD=
- WAVES__REST_API__API_KEY_HASH=

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