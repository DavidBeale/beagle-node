# crypto-node
BealgeBone Black based Cryptocurrency node


## BOM
1. [BeagleBone Black](http://beagleboard.org/BLACK) x1
2. Case [bb100](http://www.logicsupply.com/uk-en/components/beaglebone/boards-cases-kits/bb100/) x1
3. 64GB Class 10 microSD card x1 

## Installation

### OS
Ubuntu for BeagleBone Blach, flashed to eMMC - [Instructions](http://elinux.org/BeagleBoardUbuntu#eMMC:_BeagleBone_Black)

### Update OS
```shell
sudo apt-get update
sudo apt-get upgrade
```

### Build Tools
```shell
sudo apt-get install build-essential libboost-dev libdb-dev automake pkg-config
```

### SD Card mount
```shell
sudo mkdir /sd
```

### Swap Memory

### Compile bitcoind
```shell
sudo mkdir /sd/src/bitcoind
cd /sd/src/bitcoind
wget https://github.com/bitcoin/bitcoin/archive/v0.9.4.zip  # Check for a newer version
unzip v0.9.4.zip
cd bitcoin-0.9.4
./autogen.sh
./configure –disable-wallet --with-incompatible-bdb
make # This will take a long time!
cd src
strip bitcoind
```

### Setup bitcoind
