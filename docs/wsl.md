# Windows Subsystem for Linux (WSL)

→ [docs.microsoft.com](https://docs.microsoft.com/en-us/windows/wsl/)

## Installation

→ [Installation Guide for Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

### WSL 2

If your OS version is compatible, you should update to WSL 2: [Updating the WSL 2 Linux kernel](https://docs.microsoft.com/en-us/windows/wsl/wsl2-kernel)

## Learn

→ [Microsoft learn > Get started](https://docs.microsoft.com/en-us/learn/modules/get-started-with-windows-subsystem-for-linux/)

### Readings

- Microsoft
  - [Windows Subsystem for Linux Documentation](https://docs.microsoft.com/en-us/windows/wsl/about)
- Scott Hanselman
  - [The year of Linux on the (Windows) Desktop - WSL Tips and Tricks](https://www.hanselman.com/blog/TheYearOfLinuxOnTheWindowsDesktopWSLTipsAndTricks.aspx)
  - [Using Enhanced Mode Ubuntu 18.04 for Hyper-V on Windows 10](https://www.hanselman.com/blog/UsingEnhancedModeUbuntu1804ForHyperVOnWindows10.aspx)

## Tips

- Access Linux files from Windows system: open `\\wsl$\Ubuntu\` in Windows Explorer (or `%LOCALAPPDATA%\Packages\CanonicalGroupLimited.UbuntuonWindows*\LocalState\rootfs`)
- Access Windows files from Linux subsystem: go to `/mnt/c/users/<username>`

## Known issues

- Incorrect date with WSL 2: [issue #5324](https://github.com/microsoft/WSL/issues/5324), [issue #4245](https://github.com/microsoft/WSL/issues/4245)

```bash
# temporary fix, to be run regularly
sudo hwclock -s
```

- Memory issue
  - [Memory Reclaim in the Windows Subsystem for Linux 2](https://devblogs.microsoft.com/commandline/memory-reclaim-in-the-windows-subsystem-for-linux-2/) - October 30th, 2019
  - [Taking Back Memory From Vmmem/WSL](https://blog.simonpeterdebbarma.com/2020-04-memory-and-wsl/) - April 07, 2020
  
```bash
wsl --shutdown
```

- Zombie process

```bash
ps axo stat,ppid,pid,comm | grep -w defunct
sudo kill -9 <pid>
```

- Docker compose error: [issue #7899](https://github.com/docker/compose/issues/7899)

## Recipes

### Kubernetes

- [WSL+Docker: Kubernetes on the Windows Desktop](https://kubernetes.io/blog/2020/05/21/wsl-docker-kubernetes-on-the-windows-desktop/) - May 21, 2020
  - Issues with Minikube and systemd (to be validated against Ubuntu 20.04): [forum.snapcraft.io](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033/39), [DamionGans/ubuntu-wsl2-systemd-script](https://github.com/DamionGans/ubuntu-wsl2-systemd-script), [snapcraft.ninja](https://snapcraft.ninja/2020/08/06/starting-systemd-in-wsl-when-you-login-to-windows-youll-be-astounded-by-the-speed-improvement/)
  
### Connect to Windows Minikube

- In Windows, look at the kube config

```bash
kubectl config view
```

- In Ubuntu, configure the kube context

```bash
kubectl config set-cluster minikube --server=https://127.0.0.1:<port> --certificate-authority=/mnt/c/Users/<username>/.minikube/ca.crt
kubectl config set-credentials minikube --client-certificate=/mnt/c/Users/<username>/.minikube/profiles/minikube/client.crt --client-key=/mnt/c/Users/<username>/.minikube/profiles/minikube/client.key
kubectl config set-context minikube --cluster=minikube --user=minikube
kubectl config use-context minikube
kubectl get nodes
kubectl version
```

### Connect to Windows Docker (WSL 1)

- In Docker settings, make sure to expose the daemon (in Settings > General > Expose daemon on tcp://localhost:2375 without TLS)
- In Linux, make sure the DOCKER_HOST environment variable is set (`echo $DOCKER_HOST` => localhost:2375)

### Theming

- [Moving Your JavaScript Development To Bash On Windows](https://www.smashingmagazine.com/2019/09/moving-javascript-development-bash-windows/) - September 11, 2019
- [spboyer/dotnetconf-wsl-theme](https://github.com/spboyer/dotnetconf-wsl-theme)
