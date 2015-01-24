# beagle-node
BeagleBone Black based Cryptocurrency node


## BOM
1. [BeagleBone Black](http://beagleboard.org/BLACK) x1
2. Case [bb100](http://www.logicsupply.com/uk-en/components/beaglebone/boards-cases-kits/bb100/) x1
3. 64GB Class 10 microSD card x1 
4. Small Heatsink x1
5. Thermal Paste x1

## Hardware Installation

1. Attach the Heatsink to the CPU, and any other near by chips you can cover.
2. Place the board into the case.
3. Insert the SD card.
4. Attach network and power cables.


## Software Installation

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

### SD Card Mount
```shell
sudo mkdir /sd
sudo mount /dev/mmcblk0p1 /sd
sudo echo /dev/mmcblk0p1	/sd	ext4	defaults	0 0 >> /etc/fstab
```

### Swap Memory
```shell
sudo fallocate -l 2G /sd/swapfile
sudo chmod 0600 /sd/swapfile
sudo mkswap /sd/swapfile
sudo swapon /sd/swapfile
```

### Compile bitcoind
```shell
sudo mkdir /sd/bitcoind
sudo mkdir /sd/bitcoind/src
sudo chown ubuntu:ubuntu /sd/bitcoind/src
cd /sd/bitcoind/src
wget https://github.com/bitcoin/bitcoin/archive/v0.9.4.zip  # Check for a newer version
unzip v0.9.4.zip
cd bitcoin-0.9.4
./autogen.sh
./configure --disable-wallet --with-incompatible-bdb
make # This will take a long time!
cd src
strip bitcoind
```

### bitcoind User
```shell
```

### Setup bitcoind
```shell
sudo mkdir /sd/bitcoind/bin
sudo chown bitcoind:bitcoind /sd/bitcoind/bin
```
