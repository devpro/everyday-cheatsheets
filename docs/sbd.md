# Single-board computer (SBD)

Reference: [Wikipedia](https://en.wikipedia.org/wiki/Single-board_computer)

## Families

### Raspberry Pi

#### Quick start

- Prepare SD card (see [Installing operating system images](https://www.raspberrypi.org/documentation/installation/installing-images/README.md))
  - Download [Raspberry Pi Imager](https://www.raspberrypi.org/blog/raspberry-pi-imager-imaging-utility/) from [Downloads](https://www.raspberrypi.org/downloads/)
  - Look at available images on [Downloads](https://www.raspberrypi.org/downloads/)
    - [Raspberry Pi OS (previously called Raspbian)](https://www.raspberrypi.org/downloads/raspberry-pi-os/)
    - Ubuntu: follow the procedure described on [Ubuntu website](https://ubuntu.com/tutorials/how-to-install-ubuntu-core-on-raspberry-pi#1-overview).
  - Insert the SD card and run the Raspberry Pi Imager
  - Validated configurations
  
  Type | CPU | RAM | OS
  ---- | --- | --- | --
  Pi Model B Rev 2 | BCM2835 ARMv6 1176JZF-S 700 MHz | 512 Mo | Raspberry Pi OS Lite (32-bit)
  Pi Model 2 B | BCM2836 ARMv7 Cortex-A7 Quad Core 900MHz | 1 Go | Ubuntu Server 20.04 LTS (32-bit)
  
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

### Odroid

Reference: [Wikipedia](https://en.wikipedia.org/wiki/ODROID)

#### Quick start

##### Ubuntu 18.04

- Prepare the SD card
  - Download and install a flash program, such as [Etcher](https://www.balena.io/etcher/) (for example `balenaEtcher-Setup-1.5.101.exe` on Windows 10)
  - Download an image of Ubuntu minimal, such as [20190910-minimal](https://wiki.odroid.com/odroid-xu4/os_images/linux/ubuntu_4.14/20190910-minimal) (for example `ubuntu-18.04.3-4.14-minimal-odroid-xu4-20190910.img`)
  - Plug the SD card and flash it by selecting the downloade image
- Insert the SD card in the board, plug a keyboard (USB) and a monitor (HDMI) then plug the power cable
  - After few seconds a login input will be needed (root/odroid)
  - If needed, update keyboard layout
  
  ```bash
  sudo vi /etc/default/keyboard
  # update XKBLAYOUT to "fr" for a French keyboard
  sudo reboot
  ```
  
  - Change server name (and add other server name resolution with their future IP 10.0.0.X)
  
  ```bash
  sudo vi /etc/hostname
  sudo vi /etc/hosts
  sudo reboot
  ```

  - Installing a Wifi adapter can be tricky, so we first plug an ethernet connection on USB (for example, by sharing the internet connection from a mobile phone with an USB cable)
  
  ```bash
  # Make sure the USB element is recoginzed
  lsusb
  
  # Review Wifi configuration
  iwconfig
  
  # Install ifconfig
  sudo apt install net-tools
  ifconfig
  
  # Update Ubuntu packages and distribution
  sudo apt update
  sudo apt upgrade
  sudo apt dist-upgrade
  sudo reboot
  ```
  
  - Plug the Widi adapter, make sure it's up (light on?)
  
  - Ubuntu now uses [Netplan](https://netplan.io/) (see [odroid forum topic](https://forum.odroid.com/viewtopic.php?t=30766) and [configserverfirewall post](https://www.configserverfirewall.com/ubuntu-linux/configure-ubuntu-server-static-ip-address/))
  
    - Create `/etc/netplan/config.yaml`
  
    ```bash
    network:
      version: 2
      renderer: networkd
      ethernets:
        eth0:
          optional: true
          dhcp4: no
          addresses: [10.0.0.1/24]
          gateway4: 10.0.0.1
          nameservers:
            addresses: [10.0.0.1, 8.8.8.8]
      wifis:
        wlan0:
          optional: true
          dhcp4: no
          dhcp6: no
          addresses: [192.168.86.139/24]
          gateway4: 192.168.86.1
          nameservers:
            addresses: [8.8.8.8, 4.4.4.4]
          access-points:
            "mywifiname":
              password: "mypassword"
    ```
  
    - Check internet connection and enable SSH (see [2daygeek post](https://www.2daygeek.com/enable-disable-up-down-nic-network-interface-port-linux-using-ifconfig-ifdown-ifup-ip-nmcli-nmtui/))
    
    ```bash
    # Apply configuration change
    sudo netplan apply
    
    # Check IP
    ip a
    ping google.com
    
    # Look at available wifi networks
    iwlist scan
    
    # Enable network (multiple solutions)
    ip link set wlan0 up # doesn't work on my config
    nmtui
    
    # If there are any issues, deactivate DHCP and enable it afterwards
    
    # Look at services
    systemctl list-unit-files | grep enabled
    
    # Allow SSH in firewall
    sudo apt install openssh-server
    sudo apt install ufw
    sudo ufw enable
    sudo ufw allow ssh
    
    # Check service status
    sudo systemctl status ssh
    sudo service ssh status
    
    # Check opened ports
    sudo netstat -plnt
    ````
