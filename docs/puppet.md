# Puppet

→ [puppet.com](https://puppet.com/)

## Learn

Puppet is a solution to automate the management of an infrastructure, it is an open source product with an important community. Current version is 6.3 (February 2019).
An enterprise edition is available with additional features that ease the use of the solution.

Entry points:

- [Puppet documentation](https://puppet.com/docs/puppet/latest)
- [Puppet training](https://learn.puppet.com/)
- [Presentation Dojo devpro](https://slides.com/devprofr/dojo-puppet)

### Architecture

Puppet is relying on the **agent-master** pattern:

1. An agent node sends a requests (with `facts`) to the master and asks for the desired state (`catalog`)
2. The master checks the node is known (and the communication is secured with HTTPS/certificate) and sends back the catalog based on its data repository (including the code to achieve the different configurations)
3. The agent applies the catalog and reports back the result of the actions

The Puppet master is also known as the `puppetserver`.

### Modules

#### Puppet Forge

Puppet is modular by design, first step is to look at existing modules for your needs (NB: don't reinvent the wheel and keep you code on added value). Module repository is Puppet forge at [forge.puppet.com](https://forge.puppet.com/).

Interesting modules:

Name | Detail | Source |
---- | ------ | ------ |
[`puppetlabs/stdlib`](https://forge.puppet.com/puppetlabs/stdlib) | Standard library of resources for Puppet modules. | [github](https://github.com/puppetlabs/puppetlabs-stdlib)
`puppet-archive` | Compressed archive file download and extraction with native types/providers for Windows and Unix | [forge.puppet.com](https://forge.puppet.com/puppet/archive)
`puppet-download_file` | |
`puppetlabs-acl` | |
[`puppet-dotnet`](https://forge.puppet.com/puppet/dotnet) | Module to manage the Microsoft .NET framework | |
`puppet-windows_env` | |
`puppetlabs-powershell` | |
`puppetlabs-registry` | |
[`puppetlabs-iis`](https://forge.puppet.com/puppetlabs/iis) | Manage IIS for Windows Server 2008R2, 2012 and 2012R2. Maintain application sites, pools, installation, and many other IIS settings. |

#### Module creation

- [Module fundamentals](https://puppet.com/docs/puppet/6.3/modules_fundamentals.html)
- Roles and profiles, a concrete example by Puppet ([intro](https://puppet.com/docs/pe/2017.2/r_n_p_intro.html), [example](https://puppet.com/docs/pe/2017.2/r_n_p_full_example.html), [profiles](https://puppet.com/docs/pe/2017.2/r_n_p_profiles.html))

### Pipeline

- [Continuous Deployment with Jenkins](https://www.slideshare.net/PuppetLabs/stephen-connolly)

### PDK (Puppet Development Kit)

- [Welcome to Puppet Development Kit](https://puppet.com/docs/pdk/1.x/pdk.html)
- [A guide to converting a module with PDK](https://puppet.com/blog/guide-converting-module-pdk)

### Bolt

- [Welcome to Bolt](https://puppet.com/docs/bolt/latest/bolt.html)
- [Check out the latest in Puppet Bolt](https://puppet.com/blog/check-out-latest-puppet-bolt)

### Tasks

- [Puppet tasks](https://puppet.com/docs/puppet/6.3/puppet_tasks.html)
- [Easily automate ad hoc work with new Puppet Tasks](https://puppet.com/blog/easily-automate-ad-hoc-work-new-puppet-tasks)

### r10k

- [puppetlabs/r10k](https://github.com/puppetlabs/r10k)
- [Managing code with r10k](https://puppet.com/docs/pe/2018.1/r10k.html)

### Training

- Puppet ([Course Catalog](https://learn.puppet.com/course-catalog))
  - [Self-paced Training](https://learn.puppet.com/category/self-paced-training)

### Azure

- [Azure Marketplace Image User Guide](https://puppet.com/docs/azure/1.0/azure_user_guide.html)

### Usecases

- [Using Node-Side Secrets with Puppet](https://puppet.com/blog/using-node-side-secrets-puppet)
- [Puppet server installation on CentOS](https://github.com/devpro/simple-howtos/blob/master/puppet/server-installation-centos.md)

### Docker

- [puppetlabs/pupperware](https://github.com/puppetlabs/pupperware/)
  - On Windows, edit the two files:

```yaml
# docker-compose.override.yml
version: '3.5'
```

```yaml
# docker-compose.yml
version: '3.5'
services:
   puppet:
     volumes:
       - /d/Projects/bthomas/opensource/pupperware/volumes/code:/etc/puppetlabs/code/
   networks:
     - proxynet

   postgres:
     ports:
       - 5432:5432
     networks:
       - proxynet

   puppetdb:
     hostname: puppetdb
     depends_on:
       - postgres
       - puppet
     networks:
       - proxynet

networks:
  proxynet:
    name: custom_network
```

## Practice

- [devpro/puppet-training-beginner](https://github.com/devpro/puppet-training-beginner)

## Unit testing

### Documentation

- [RSPEC-PUPPET](http://rspec-puppet.com/)
- [puppetlabs/puppetlabs_spec_helper](https://github.com/puppetlabs/puppetlabs_spec_helper)

### Files

- `.fixture.yml` file is where you can declare dependencies with other modules

  ```ini
  ---
  fixtures:
    forge_modules:
      stdlib: "puppetlabs/stdlib"
    symlinks:
      profile: "#{source_dir}/../../site/profile"
  ```

## Puppet agent

### Installation on [Windows](https://puppet.com/docs/puppet/latest/install_windows.html)

Go to [Download page](https://downloads.puppetlabs.com/windows/puppet5/) and select the version that you need (`puppet-agent-x64-latest.msi` for example).

```bash
# install the puppet agent
msiexec /qn /norestart /i path\to\puppet-agent-5.X.Y-x64.msi PUPPET_MASTER_SERVER=mypuppetmastername /l*v C:\msipuppetlog.txt
# follow the progress with C:\msipuppetlog.txt (with baretail for example), it takes severals seconds, the file should end with:
# MSI (c) (C8:DC) [10:40:39:503]: MainEngineThread is returning 0
sc config "puppet" start= disabled
sc stop "puppet"
```

#### Configuration files (Windows)

| File path                                          | Details                          |
| -------------------------------------------------- | -------------------------------- |
| `C:\Windows\System32\drivers\etc\hosts`            | Host file                        |
| `C:\Users\xxxxxxx\.gitconfig`                      | Git configuration file           |
| `C:\ProgramData\PuppetLabs\puppet\etc\puppet.conf` | Puppet agent configuration file  |
| `C:\ProgramData\PuppetLabs\puppet\etc\ssl`         | Puppet client ssl                |

#### Directory structure (Windows)

* `C:\ProgramData\PuppetLabs\code\environments`: local copy of environment files

### Agent commands

```bash
# launch manually the puppet agent
puppet agent --test

# launch locally puppet code (no puppet server needed), see https://puppet.com/docs/puppet/5.3/man/apply.html
puppet apply --modulepath="modules;site" --hiera_config="hiera.yaml" .\manifests\site.pp

# display active configuration
puppet config print

# get information on the machine the way Puppet does
facter

# facts ([man page](https://puppet.com/docs/puppet/5.3/man/facts.html))
puppet facts

# retrieve modules from the [Puppetfile](https://github.com/puppetlabs/r10k/blob/master/doc/puppetfile.mkd)
r10k puppetfile install -v

# PDK command lines
pdk new module
pdk new class mymodule
pdk new class mymodule::myfolder::myclass
pdk validate
pdk test unit

# list all installed applications
puppet resource package
# list of defined services and their status
puppet resource service

# display fact path
puppet agent --configprint factpath
```

## Puppet server

It is also known as **Puppet master**.
You can review the procedure to install a Puppet server on this [page](./server_installation_centos.md).

### Server commands (CentOS)

```bash
# start puppet server
service puppetserver start
# systemctl start puppetserver.service

# get puppet server service info
service puppetserver status
# shortcut for systemctl status puppetserver.service

# stop puppet server
service puppetserver stop
# systemctl stop puppetserver.service

# get logs from system journal
journalctl -xe

# get puppet agent service info
service puppet status

# executes r10k ([usage](https://github.com/puppetlabs/r10k/blob/master/doc/dynamic-environments/usage.mkd))
cd /etc/puppetlabs/r10k
sudo /opt/puppetlabs/puppet/bin/r10k deploy environment --puppetfile

# list certificates to be validated
sudo /opt/puppetlabs/puppet/bin/puppet cert list

# sign a certificate
sudo /opt/puppetlabs/puppet/bin/puppet cert sign xxxxxx

# follow logs in real time
tail -f /var/log/puppetlabs/puppetserver/puppetserver.log
tail -f /var/log/puppetlabs/puppetserver/puppetserver-access.log
```

### Configuration files ([doc](https://puppet.com/docs/puppetserver/5.1/configuration.html))

| File path                                       | Details                                 |
| ----------------------------------------------- | --------------------------------------- |
| `/etc/sysconfig/puppetserver`                   | Puppet server configuration file        |
| `/etc/puppetlabs/puppetserver/conf.d/auth.conf` | Puppet serveur auth configuration file ([doc](https://puppet.com/docs/puppetserver/5.1/config_file_auth.html)) |
| `/etc/puppetlabs/puppet/puppet.conf`            | Puppet agent configuration file         |
| `/etc/puppetlabs/puppet/hiera.yaml`             | Hiera configuration file ([doc](https://puppet.com/docs/puppet/5.3/hiera_intro.html)) |
| `/etc/puppetlabs/r10k/r10k.yaml`                | r10k configuration                      |

### Directory structure

* `/etc/puppetlabs`: base path
* `/etc/puppetlabs/code`: Puppet code managed by git, this is where r10k will
* `/etc/puppetlabs/code/environments`: Definition per environment, this is where r10k will create folders per git repository branches (production, staging, etc.)
* `/etc/puppetlabs/puppet`: Puppet Agent configuration
* `/etc/puppetlabs/puppetserver`: PuppetServer configuration
* `/etc/puppetlabs/puppetserver/conf.d`: Settings (see [Puppet Server Configuration](https://puppet.com/docs/puppetserver/5.1/configuration.html))
* `/etc/puppetlabs/r10k`: r10k configuration
* `/opt/puppetlabs`: Internal Puppet stuff, binaries, etc
* `/var/log/messages`: Puppet Agent logs
* `/var/log/puppetlabs`: Other logging
* `/tmp`: Used by the installer (issues if set ‘noexec’)

You can read [Magic directories: a guide to Puppet directory structure](https://puppet.com/blog/magic-directories-guide-to-puppet-directory-structure).

## Terminology

* r10k [puppet.com](https://puppet.com/blog/git-workflows-puppet-and-r10k)
