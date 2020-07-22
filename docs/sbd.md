# Single-board computer (SBD)

Reference: [Wikipedia](https://en.wikipedia.org/wiki/Single-board_computer)

## Families

### Raspberry Pi

#### Quick start

- Prepare SD card
  - Download [Raspberry Pi Imager](https://www.raspberrypi.org/blog/raspberry-pi-imager-imaging-utility/), available in [downloads](https://www.raspberrypi.org/downloads/)
  - Follow the procedure described on [Ubuntu website](https://ubuntu.com/tutorials/how-to-install-ubuntu-core-on-raspberry-pi#1-overview).

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

  - Installing a Wifi adapter can be tricky, so we first plug an ethernet connection on USB (for example, by sharing the internet connection from a mobile phone with an USB cable)
  
  ```bash
  lsusb
  iwconfig
  sudo apt install net-tools
  ifconfig
  sudo apt update
  sudo apt upgrade
  sudo apt dist-upgrade
  sudo reboot
  ```
  
  - Plug the Widi adapter, make sure it's up (light?)
  
  - Ubuntu now uses [Netplan](https://netplan.io/) (see [odroid forum topic](https://forum.odroid.com/viewtopic.php?t=30766) and [configserverfirewall post](https://www.configserverfirewall.com/ubuntu-linux/configure-ubuntu-server-static-ip-address/))
  
    - Create `/etc/netplan/config.yaml`
  
    ```bash
    network:
      version: 2
      renderer: networkd
      wifis:
        wlan0:
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
  
    - Check internet connection and enable SSH
    
    ```bash
    # Apply configuration change
    sudo netplan apply
    
    # Check IP
    ip addr
    ping google.com
    
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
