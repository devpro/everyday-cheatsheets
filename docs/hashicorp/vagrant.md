# Vagrant

> Vagrant enables the creation and configuration of lightweight, reproducible, and portable development environments.

→ [vagrantup.com](https://www.vagrantup.com/)

## Learn

### Boxes

> Boxes are the package format for Vagrant environments. A box can be used by anyone on any platform that Vagrant
supports to bring up an identical working environment.  
> HashiCorp (the makers of Vagrant) publish a basic Ubuntu 18.04 64-bit box that is available for minimal use cases.
It is highly optimized, small in size, and includes support for VirtualBox, Hyper-V, and VMware.

→ [vagrantup.com/docs/boxes](https://www.vagrantup.com/docs/boxes)

### CLI

Command              | Action | Link(s)
-------------------- | ------ | -------
`vagrant box add`    |        | [docs](https://www.vagrantup.com/docs/cli/box)
`vagrant init`       |        | [docs](https://www.vagrantup.com/docs/cli/init)
`vagrant up`         |        |
`vagrant ssh`        |        |
`vagrant suspend`    |        |
`vagrant destroy`    |        |
`vagrant ssh-config` |        |
`vagrant box list`   |        |

### Images

- [Bento](https://app.vagrantup.com/bento) ([GitHub](https://github.com/chef/bento))

### Samples

- [rcloutier/linux-vm](https://gitlab-ncsa.ubisoft.org/rcloutier/linux-vm)

## Get started

### Working with Vagrant inside of WSL2

Solution found on [github.com](https://github.com/geerlingguy/ansible-for-devops/issues/291#issuecomment-815253528)

### Ubuntu 20.04 with VirtualBox

- [Getting Started](https://learn.hashicorp.com/collections/vagrant/getting-started)

- Commands from a specific folder (needs elevated permissions on Windows)

```bash
# adds a box
vagrant box add hashicorp/bionic64

# initializes a local configuration
vagrant init hashicorp/bionic64

# in case of WSL2 add the following line (without the # at the beginning) to Vagrantfile
#  config.ssh.insert_key = false

# creates the machine(s) (if asked, provide UBISOFT-ORG\flastname and AD password)
vagrant up

# connects the machine(s)
vagrant ssh

# suspends the machine(s)
vagrant suspend

# resumes the machine(s)
vagrant resume

# destroys the machine(s)
vagrant destroy
```

### Hyper-V specificities

- [Learning to Use Vagrant on Windows 10](
https://docs.microsoft.com/en-us/virtualization/community/team-blog/2017/20170706-vagrant-and-hyper-v-tips-and-tricks)

- Add provider CLI parameter

```bash
# example
vagrant box add hashicorp/bionic64 --provider hyperv
```

- Add lines in the Vagrantfile

```vagrantfile
# Vagrantfile
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"
  config.vm.provider "hyperv"
  # private network won't work
  config.vm.network "public_network"
  # workaround to avoid "mount error(13): Permission denied. Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)"
  config.vm.synced_folder ".", "/vagrant", disabled: true
end
```

- If an authentication is asked, provide UBISOFT-ORG\shortusername and AD password

## Providers

### Hyper-V

- [Configuration](https://www.vagrantup.com/docs/hyperv/configuration.html)
- [Boxes](https://app.vagrantup.com/boxes/search?provider=hyperv)
- [Limitations](https://www.vagrantup.com/docs/hyperv/limitations.html)
- [FollowKMan - Vagrant up on Windows 10 with Hyper-V](https://followkman.com/2016/07/27/vagrant-up-on-windows-10-with-hyper-v/)
- [Vagrant and Hyper-V -- Tips and Tricks](https://techcommunity.microsoft.com/t5/virtualization/vagrant-and-hyper-v-tips-and-tricks/ba-p/382373) - March 21, 2019
