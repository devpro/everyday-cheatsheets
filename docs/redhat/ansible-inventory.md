# Ansible Inventory

> Ansible works against multiple managed nodes or “hosts” in your infrastructure at the same time, using a list or group of lists known as inventory. Once your inventory is defined, you use patterns to select the hosts or groups you want Ansible to run against.

→ [docs.ansible.com](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)

## Inventory types

Inventory can be static or dynamic (stored in EC2 for example).

## Inventory plugins

> Inventory plugins allow users to point at data sources to compile the inventory of hosts that Ansible uses to target tasks, either using the -i /path/to/file and/or -i 'host1, host2' command line parameters or from other configuration sources.

→ [docs.ansible.com](https://docs.ansible.com/ansible/latest/plugins/inventory.html)

## Examples of inventory plugins

* EC2 inventory source: [amazon.aws.aws_ec2](https://docs.ansible.com/ansible/latest/collections/amazon/aws/aws_ec2_inventory.html)
* Azure Resource Manager inventory plugin: [azure.azcollection.azure_rm](https://docs.ansible.com/ansible/latest/collections/azure/azcollection/azure_rm_inventory.html#ansible-collections-azure-azcollection-azure-rm-inventory)
