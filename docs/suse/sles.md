# SUSE Linux Enterprise Server (SLES)

## Commands

```bash
# adds main repository (see https://en.opensuse.org/Package_repositories)
zypper addrepo http://download.opensuse.org/distribution/leap/15.3/repo/oss/ oss

# lists updates
zypper list-updates

# refreshes package list
zypper refresh

# update packages
zypper up

# installs a package (git here)
sudo zypper install git
```
