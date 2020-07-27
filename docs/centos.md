# CentOS (Community Enterprise Operating System)

Fedora is the community distribution that forms the basis of CentOS.

CentOS is RPM-based and uses yum.

## Commands

### General

```bash
# get information on running CentOS
cat /etc/centos-release
# switch between keyboard layouts
loadkeys fr
# look at drive disk space
df -h
```

### Packages

```bash
sudo yum install sysstat
mpstat
```

### Network

```bash
# display general network info
ifconfig
# when you edit a network config
service network restart
# check SSH daemon status
service sshd status
# stop/disable the firewall
systemctl stop firewalld
systemctl disable firewalld
```


<details>
  <summary>Example of /etc/sysconfig/network-scripts/ifcfg-xxxx</summary>

  ```ini
  TYPE=Ethernet
  PROXY_METHOD=none
  BROWSER_ONLY=no
  BOOTPROTO=static
  DEFROUTE=yes
  IPV4_FAILURE_FATAL=no
  IPV6INIT=yes
  IPV6_AUTOCONF=yes
  IPV6_DEFROUTE=yes
  IPV6_FAILURE_FATAL=no
  IPV6_ADDR_GEN_MODE=stable-privacy
  NAME=xxxx
  UUID=xxxx-xxxxx-xxxxxx
  DEVICE=xxxx
  ONBOOT=yes
  IPADDR=10.115.100.91
  PREFIX=24
  GATEWAY=10.115.100.254
  DNS1=10.115.100.1
  DOMAIN=mydomain.lan
  ```
  
</details>

### User

```bash
# give a user sudo permission (wheel group created by default)
sudo usermod -a -G wheel myusername
# review sudo config
cat /etc/sudoers
```

### Services

```bash
# look at services
chkconfig
# get current run level
runlevel
# get all existing services
service --status-all
```
