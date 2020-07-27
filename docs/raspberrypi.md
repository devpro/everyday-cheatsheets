# Raspberry Pi

## Quick start

### Operating system choice

Reference: [Installing operating system images](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)

#### Validated configurations
  
Type | CPU | RAM | OS
---- | --- | --- | --
Pi Model B Rev 2 | BCM2835 ARMv6 1176JZF-S 700 MHz | 512 Mo | Raspberry Pi OS Lite (32-bit)
Pi Model 2 B | BCM2836 ARMv7 Cortex-A7 Quad Core 900MHz | 1 Go | Ubuntu Server 20.04 LTS (32-bit)
  
#### SD card preparation

- Download [Raspberry Pi Imager](https://www.raspberrypi.org/blog/raspberry-pi-imager-imaging-utility/) from [Downloads](https://www.raspberrypi.org/downloads/)
- Look at available images on [Downloads](https://www.raspberrypi.org/downloads/)
  - [Raspberry Pi OS (previously called Raspbian)](https://www.raspberrypi.org/downloads/raspberry-pi-os/)
  - [Ubuntu](https://ubuntu.com/tutorials/how-to-install-ubuntu-core-on-raspberry-pi#1-overview).
- Insert the SD card and run the Raspberry Pi Imager

### Initial boot

- Insert the SD card in the board, plug a keyboard (USB), a monitor (HDMI), a WIFI then plug the power cable

#### Raspberry Pi OS (Debian 10 = Buster)

  - System update
  
  ```bash
  # login with pi/raspberry

  # look at the system information (for example Raspbian 10 buster = Debian for Raspberry Pi)
  lsb_release -a

  # change the keyboard layout
  sudo vi /etc/default/keyboard
  # update XKBLAYOUT to "fr" for a French keyboard
  sudo reboot

  # configuration the easy way: configure Wifi, update hostname, enable SSH, change password, (optional) keyboard configuration
  raspi-config
  
  # (optional) set static ip address with the lines below
  sudo nano /etc/dhcpcd.conf
  sudo reboot
  ```
  
  - Network configuration (`/etc/dhcpcd.conf`)
  
  ```ini
  interface wlan0
  static ip_address=192.168.86.145/24
  static routers=192.168.86.1
  static domain_name_servers=192.168.86.1 8.8.8.8 4.4.4.4
  ```
  
  - Install .NET Core doesn't work even by grabbing [Downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1) > [ARM32 versions](https://dotnet.microsoft.com/download/dotnet-core/thank-you/sdk-3.1.302-linux-arm32-binaries) as [ARMv6 is not supported](https://github.com/dotnet/runtime/issues/7764)

#### Ubuntu Server (20.04 LTS)

  - System update
  
  ```bash
  # login with ubuntu/ubuntu
  
  # look at the processors
  cat /proc/cpuinfo
  
  # change the keyboard layout
  sudo vi /etc/default/keyboard
  # update XKBLAYOUT to "fr" for a French keyboard
  sudo dpkg-reconfigure keyboard-configuration
  sudo reboot
  
  # configure Wifi
  ls /sys/class/net
  sudo ip link set wlan0 up
  sudo nano /etc/netplan/01-config.yaml
  sudo netplan apply
  sudo reboot
  
  # SSH should be available
  ip a
  
  # run system updates
  sudo apt update
  sudo apt upgrade
  sudo apt dist-upgrade
  sudo reboot
  ```
  
   - Install .NET Core
   
  ```bash
  # official procedure doesn't work: https://docs.microsoft.com/en-us/dotnet/core/install/linux-ubuntu
  
  # link taken by following download link from https://dotnet.microsoft.com/download/dotnet-core/3.1
  wget https://download.visualstudio.microsoft.com/download/pr/56691c4c-341a-4bca-9869-409803d23cf8/d872d7a0c27a6c5e9b812e889de89956/dotnet-sdk-3.1.302-linux-arm.tar.gz
  mkdir -p $HOME/dotnet
  tar -xvf dotnet-sdk-3.1.302-linux-arm.tar.gz -C $HOME/dotnet
  export DOTNET_ROOT=$HOME/dotnet
  export PATH=$PATH:$HOME/dotnet
  dotnet --version
  
  # add the two export lines in .bashrc so it will be permanent
  nano .bashrc
  
  cat << \EOF >> ~/.profile
  
  # add .NET Core SDK
  export DOTNET_ROOT=$HOME/dotnet
  export PATH=$PATH:$HOME/dotnet
  
  # add .NET Core SDK tools
  export PATH="$PATH:$HOME/.dotnet/tools"
  EOF
  
  logout
  ```
  
