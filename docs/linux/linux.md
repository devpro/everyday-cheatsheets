# Linux operating systems

## Distributions

- Debian
  - [Ubuntu](./ubuntu.md)
- Fedora
  - Red Hat Enterprise Linux (RHEL)
    - [CentOS](./centos.md)
    - [Rocky](./rocky.md)
- openSUSE

## Common utilities

- `systemd`

- `journald`

- `firewalld`

- `ip`

- `uname`

- `df`

- `free`

- `less /proc/meminfo`

- `more /proc/cpuinfo`

- `cat /proc/version`

## Usual commands

```bash
# get information on the kernel
uname -or

# get server name
hostname
uname -n

# get information on a user
id
id otherusername

# update my password
passwd

# add a user (the user will be locked and we need to define its password with passwd)
useradd xxx

# extend admin permission for 5 minutes
sudo -v

# live monitoring of processes
top
```

## Common packages

Name | Details
---- | -------
**wget** | GNU Wget is a free software package for retrieving files using HTTP, HTTPS, FTP and FTPS the most widely-used Internet protocols

## Shell shortcuts

Shortcut | Action
-------- | ------
`Ctrl` + `R` | Search a command in the history
