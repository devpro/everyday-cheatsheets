# Ansible

> Simple, agentless IT automation that anyone can use. Ansible is a universal language, unraveling the mystery of how work gets done. Turn tough tasks into repeatable playbooks. Roll out enterprise-wide protocols with the push of a button.

→ [ansible.com](https://www.ansible.com/), [github.com](https://github.com/ansible/ansible), [docs.ansible.com](https://docs.ansible.com/)

## Learn

### Documentation

* [Ansible Community](https://docs.ansible.com/ansible/latest/index.html)
* [Ansible Core](https://docs.ansible.com/ansible-core/devel/index.html)

### Concepts

* Control nodes

  > Any machine with Ansible installed. Ansible commands and playbooks can be run by invoking the ansible or ansible-playbook command from any control node (any computer that has a Python installation). Having multiple control nodes is possible.

* Managed nodes

  > The network devices (and/or servers) managed with Ansible. Managed nodes are also sometimes called “hosts”. Ansible is not installed on managed nodes.

* [Inventory](./ansible-inventory.md)

  > A list of managed nodes. An inventory file is also sometimes called a “hostfile”. The inventory can specify information like IP address for each managed node. An inventory can also organize managed nodes, creating and nesting groups for easier scaling.

* [Collections](./ansible-collections.md)

  > Collections are a distribution format for Ansible content that can include playbooks, roles, modules, and plugins. You can install and use collections through Ansible Galaxy.

* [Modules](./ansible-modules.md)

  > The units of code Ansible executes. Each module has a particular use, from administering users on a specific type of database to managing VLAN interfaces on a specific type of network device. A single module with a task can be invoked, or several different modules in a playbook. Starting in Ansible 2.10, modules are grouped in collections.

* Tasks

  > The units of action in Ansible. A single task can be executed once with an ad hoc command.

* [Playbooks](./ansible-playbooks.md)

  > Ordered lists of tasks, saved so that those tasks in that order repeatedly. Playbooks can include variables as well as tasks. Playbooks are written in YAML and are easy to read, write, share and understand.

→ [docs.ansible.com](https://docs.ansible.com/ansible/latest/user_guide/basic_concepts.html)

### Additional content

* [Ansible CLI](./ansible-cli.md)
* [Ansible Roles](./ansible-roles.md)
* [Ansible Galaxy](./ansible-galaxy.md)

### Getting started

* [docs.ansible.com](https://docs.ansible.com/ansible/latest/user_guide/index.html#getting-started)
* [ansible.com](https://www.ansible.com/resources/get-started)

### Learning paths

* [devpro/infrastructure-automation-guide](https://github.com/devpro/infrastructure-automation-guide/blob/main/docs/learning-path.md#ansible)

### Tutorials

* [How To Manage Remote Servers with Ansible (DigitalOcean)](https://www.digitalocean.com/community/tutorial_series/how-to-manage-remote-servers-with-ansible)

### Playgrounds

* [KataCoda](https://www.katacoda.com/courses/ansible/playground) (with [Courses](https://www.katacoda.com/courses/ansible))

## Guides

### Network automation

* [docs.ansible.com](https://docs.ansible.com/ansible/latest/network/getting_started/index.html)

### Public Cloud automation

* [docs.ansible.com](https://docs.ansible.com/ansible/latest/scenario_guides/cloud_guides.html)

#### Azure

* [docs.microsoft.com](https://docs.microsoft.com/en-us/azure/developer/ansible/)

### Virtualization and Containerization automation

* [docs.ansible.com](https://docs.ansible.com/ansible/latest/scenario_guides/virt_guides.html)
