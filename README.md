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

### Update config files
Nginx. Replace `138.68.73.84` with your server ip address.
```
cd nginx
nano nginx.conf
```

Fullnode. Full-up all empty parameters.
```
cd fullnode
mv waves-fullnode.example.conf waves-fullnode.conf 
nano waves-fullnode.conf
```

### Pull docker images
Inside `/root/.waves/compose` directory run.
```
docker-compose pull
docker-compose up -d
```
☝️Current version of Waves Blockchain is 1.2

### Create your own image (optional)
This might be helpful for updating fullnode version or pushing the images to your private Docker environment. Don't forget to replace `chainify` with your account name in `docker-compose.*` files.

To build and upload your images run:
```
docker login
docker-compose -f docker-compose.dev.yml build
docker-compose -f docker-compose.dev.yml push
```


### Display fullnode logs
```
docker logs -f waves-fullnode --tail 200
```

----
MIT license