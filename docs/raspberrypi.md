# Raspberry Pi

[Raspberry Pi Foundation](https://www.raspberrypi.org/): [GitHub](https://github.com/raspberrypi), [Magazine](https://magpi.raspberrypi.org/)

## Quick start

[Documentation](https://www.raspberrypi.org/documentation/)

### Operating system setup

[Installing operating system images](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)

#### Validated configurations
  
Type | CPU | RAM | OS
---- | --- | --- | --
**Pi Model B Rev 2** | BCM2835 ARMv6 1176JZF-S 700 MHz | 512 Mo | Raspberry Pi OS Lite (32-bit)
**Pi Model 2 B** | BCM2836 ARMv7 Cortex-A7 Quad Core 900MHz | 1 Go | Ubuntu Server 18.04 (32-bit), Ubuntu Server 20.04 LTS (32-bit)
**[Pi Model 4 B](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/specifications/)** | BCM2711 ARMv8 Quad core Cortex-A72 64-bit 1.5GHz | 4 Go LPDDR4-3200 | Ubuntu Server 18.04 (64-bit), Ubuntu Server 20.04 LTS (64-bit)

#### Known issues

- **WIFI issues with Pi 4**: [tom'sHARDWARE](https://www.tomshardware.com/news/raspberry-pi-4-wi-fi-not-working), [Raspberry Pi 4 WiFi stops working at 2560x1440 screen resolution](https://www.enricozini.org/blog/2019/himblick/raspberry-pi-4-loses-wifi-at-2560x1440-screen-resolution/)
- **Display stops working after a change in the config file**: try holding the SHIFT key during startup (using this key will make the Raspberry Pi ignore the boot configuration file and load up with the default settings)

#### Key elements

#### SD card preparation

- (Optional) Download a specific version from [ubuntu.com](https://ubuntu.com/download/raspberry-pi) (for instance the previous before the LTS if it's too new for a specific hardware) WARNING links have to be modified manually (typo in pi version number...)
- Go to the [Downloads page](https://www.raspberrypi.org/downloads/)
  - Install [Raspberry Pi Imager](https://www.raspberrypi.org/blog/raspberry-pi-imager-imaging-utility/)
  - (Optional) Look at available images
    - [Raspberry Pi OS](https://www.raspberrypi.org/downloads/raspberry-pi-os/)
    - [Ubuntu](https://ubuntu.com/download/raspberry-pi) ([tutorial](https://ubuntu.com/tutorials/how-to-install-ubuntu-core-on-raspberry-pi), interesting to download a specific version, for instance to get a previous version if it's too new for a specific hardware, WARNING links have to be modified manually: there is a typo in pi version number...)
- Insert the SD card and run the Raspberry Pi Imager
- (Optional) Eject and insert again the SD card
  - Edit `network-config` at the root of the drive (with new eth0 and wlan0 parameters)

### Initial boot

- Insert the SD card in the board, plug a keyboard (USB), a monitor (HDMI) then plug the power cable

### Hardware check

_Note_: @since Kernel 4.9, BCM2835 will be displayed for the processor, even for BCM2836, BCM2837 and BCM2711. You should look instead at the [revision code](https://www.raspberrypi.org/documentation/hardware/raspberrypi/revision-codes/README.md), which is unique.

```bash
cat /proc/cpuinfo
```

### Shared steps

#### Wifi setup

```bash
# list interfaces
ls /sys/class/net

# enable an interface
sudo ip link set wlan0 up

# see the wireless interface
iwconfig

# if it doesn't show up, run
sudo ifconfig wlan0 up

# scan available networks
sudo iwlist wlan0 scan

# edit or create a netplan yaml file and apply the change
sudo nano /etc/netplan/50-cloud-init.yaml
sudo netplan -d apply
systemctl daemon-reload
sudo reboot

# look at services
sudo systemctl status systemd-networkd.service
sudo systemctl status netplan-wpa-wlan0.service

# make sure it's connected (with an IP)
ip a
ping google.com

# some Wifi USB adaptors may be incompatible with networkd, in this case fallback to NetworkManager
# - just in case make sure the value is correct (2 letter iso country code)
sudo nano /etc/default/crda
# - make sure NetworkManager service is started (start it if needed)
sudo systemctl status NetworkManager.service
# - edit netplan file to use NetworkManager instead of networkd (and comment the existing config)
sudo nano /etc/netplan/50-cloud-init.yaml
sudo netplan apply
systemctl daemon-reload
# - install additional package to have additional tools to configure wifi network
sudo apt install network-manager
# - run the configuration wizard
nmtui
# - set static ip
nmcli con mod mywifiname ipv4.addresses "192.168.86.144" ipv4.gateway "192.168.86.1" ipv4.dns "8.8.8.8,4.4.4.4" ipv4.method "manual"
# - look at the configuration file
sudo more /etc/NetworkManager/system-connections/mywifiname
# - restart the service to take this new configuration into account
sudo systemctl restart NetworkManager.service
```

#### System update

```bash
# review the operating system information
lsb_release -a

# use package manager to run updates
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
sudo reboot
```

#### Troubleshoot

```bash
# make sure all services are up
systemctl --failed

# look at recent entries in the journal
journalctl -xe
```

#### Keyboard layout configuration

```bash
sudo dpkg-reconfigure keyboard-configuration
sudo setupcon
more /etc/default/keyboard
sudo reboot
```

#### Raspberry Pi OS (aka Raspbian, Debian 10 = Buster)

- Login with `pi`/`raspberry`
- Change keyboard layout
- Configure the easy way: set Wifi parameters, update hostname, enable SSH, change password, (optional) change keyboard configuration

```bash
raspi-config
```

- (Optional] Configure a static ip by editing `/etc/dhcpcd.conf` (do a `sudo reboot` afterwards)

```ini
interface wlan0
static ip_address=192.168.86.145/24
static routers=192.168.86.1
static domain_name_servers=192.168.86.1 8.8.8.8 4.4.4.4
```

- Run updates

- Install .NET Core doesn't work even by grabbing [Downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1) > [ARM32 versions](https://dotnet.microsoft.com/download/dotnet-core/thank-you/sdk-3.1.302-linux-arm32-binaries) as [ARMv6 is not supported](https://github.com/dotnet/runtime/issues/7764)

#### Ubuntu Server (18.04)

- Login with `ubuntu`/`ubuntu` (you'll be asked to provide a new password)
- Change keyboard layout
- (Optional) Review boot log

```bash
dmesg
```

- If there is an issue starting systemd-modules, look at the journal and investigate the issue

```bash
sudo systemctl status systemd-modules-load.service

# manual step needed on Raspberry Pi 2: comment is_iser (see https://askubuntu.com/questions/877245/systemd-modules-load-failed-to-start)
sudo nano /lib/modules-load.d/open-iscsi.conf

sudo systemctl start systemd-modules-load.service
```

- Configure Wifi
- Run system updates

#### Ubuntu Server (20.04 LTS)

- Login with `ubuntu`/`ubuntu` (you'll be asked to provide a new password)
- Change keyboard layout
- Configure Wifi
- Run system updates

- Install .NET Core on ARMv7 32-bit

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

- Install .NET Core on ARMv8 64-bit

```bash
```

## Use cases

### Retro gaming

#### retropie

Home: [retropie.org.uk](https://retropie.org.uk/), [GitHub](https://github.com/RetroPie)

Configuration:
- Usability
  - [HotKeys](https://retropie.org.uk/docs/Controller-Configuration/#hotkeys)
- SSH
  - Enable SSH in raspi-config: interfacing options > SSH > Enable > reboot your pi
- [Amiga games](https://retropie.org.uk/docs/Amiga/)
  - Install [Amiberry](https://github.com/midwan/amiberry) from the optional packages
    - Follow the [guide](https://github.com/midwan/amiberry/wiki/Using-Amiberry-with-RetroPie---Installation-and-Setup)
    - Copy Amiga games (.adf, .ipf, .zip) in `/home/pi/RetroPie/roms/amiga`
    - Copy BIOS files (`kick13.rom`, `kick20.rom`, `kick31.rom`) in `/home/pi/RetroPie/BIOS`
  - Make sure you have a keyboard and a mouse :)
- `/boot/config.txt` file
  - Values
  
  Key | value | Detail | Comment
  --- | ----- | ------ | -------
  `hdmi_group` | 1 | CEA (Consumer Electronics Association) is the display standard that is typically used on a TV |
  `hdmi_group` | 2 | DMT (Display Monitor Timings) is the standard that is typically used by monitors |
  `hdmi_mode` | 16 | CEA 1920×1080 16:9 60hz |
  `hdmi_mode` | 97 | CEA 3840×2160 16:9 60hz | Raspberry Pi 4 Only. To use this hdmi_enable_4kp60=1 must be set in /boot/config.txt.
  `hdmi_mode` | 82 | DMT 1920×1080 16:9 60hz |

  - To review: hdmi_force_hotplug=1, hdmi_drive=2

Known issues:
- `Latest update lvl0: VolumeControl::init() - Failed to find mixer elements!`
  - [How to configure sound for RetroPie EmulationStation](https://retropie.org.uk/docs/Sound-Issues/)
  - `/opt/retropie/configs/all/emulationstation/es_settings.cfg`: AudioDevice=HDMI/Headphone
  - [Latest Raspberry Pi OS update – May 2020](https://www.raspberrypi.org/blog/latest-raspberry-pi-os-update-may-2020/)
  - [How-to: Use USB Audio in Retropie v3.7](https://sudomod.com/forum/viewtopic.php?t=144)
- Screen resolution
  - [Documentation > Configuration > Config-txt > Video](https://www.raspberrypi.org/documentation/configuration/config-txt/video.md)
  - `/boot/config.txt`: hdmi_group/hdmi_mode
- Messed up configuration situation
  -  SSH in (https://github.com/retropie/retropie-setup/wiki/ssh), run sudo ~/RetroPie-Setup/retropie_setup.sh and go to Emulation Station configuration via Manage Packages -> Core Packages -> emulationstation -> Configuration or Configuration / Tools -> emulationstation and choose the option to Clear/Reset Emulation Station input configuration (All packages with configuration appear in Configuration / Tools when installed)

#### Amibian

_Seems dead_

- [gunkrist79.wixsite.com/amibian](https://gunkrist79.wixsite.com/amibian)
- [Installing Amiga Workbench on Raspberry Pi with Amibian](https://stuffjasondoes.com/2018/07/18/installing-amiga-workbench-on-raspberry-pi-with-amibian/) - July 24, 2018
- [How to Emulate the Commodore Amiga on a Raspberry Pi Using Amibian](https://www.makeuseof.com/tag/emulate-amiga-raspberry-pi/) - August 15, 2018
- [Turn your Pi into an Amiga](https://magpi.raspberrypi.org/articles/turn-pi-amiga) - 2017
