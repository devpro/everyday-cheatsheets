# Windows Subsystem for Linux (WSL)

[Documentation](https://docs.microsoft.com/en-us/windows/wsl/)

## Installation

[Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

### WSL 2

If your OS version is compatible, you should update to WSL 2:

- [Updating the WSL 2 Linux kernel](https://docs.microsoft.com/en-us/windows/wsl/wsl2-kernel)

## Learn

[Microsoft learn > Get started with Windows Subsystem for Linux](https://docs.microsoft.com/en-us/learn/modules/get-started-with-windows-subsystem-for-linux/)

### Readings

- Microsoft
  - [Windows Subsystem for Linux Documentation](https://docs.microsoft.com/en-us/windows/wsl/about)
- Scott Hanselman
  - [The year of Linux on the (Windows) Desktop - WSL Tips and Tricks](https://www.hanselman.com/blog/TheYearOfLinuxOnTheWindowsDesktopWSLTipsAndTricks.aspx)
  - [Using Enhanced Mode Ubuntu 18.04 for Hyper-V on Windows 10](https://www.hanselman.com/blog/UsingEnhancedModeUbuntu1804ForHyperVOnWindows10.aspx)

## Tips

- Access Linux files from Windows system: open `\\wsl$\Ubuntu\` in Windows Explorer (or `%LOCALAPPDATA%\Packages\CanonicalGroupLimited.UbuntuonWindows*\LocalState\rootfs`)
- Access Windows files from Linux subsystem: go to `/mnt/c/users/<username>`

## Recipes

- [WSL+Docker: Kubernetes on the Windows Desktop](https://kubernetes.io/blog/2020/05/21/wsl-docker-kubernetes-on-the-windows-desktop/) - May 21, 2020

#### Connect to Windows Docker

- In Docker settings, make sure to expose the daemon (in Settings > General > Expose daemon on tcp://localhost:2375 without TLS)

- In Linux, make sure the DOCKER_HOST environment variable is set

  > $ echo $DOCKER_HOST
  >
  > localhost:2375

#### Theming

- [Moving Your JavaScript Development To Bash On Windows](https://www.smashingmagazine.com/2019/09/moving-javascript-development-bash-windows/) - September 11, 2019
- [spboyer/dotnetconf-wsl-theme](https://github.com/spboyer/dotnetconf-wsl-theme)
