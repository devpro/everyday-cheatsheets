# Ansible command line tools

→ [docs.ansible.com/user_guide/command_line_tools](https://docs.ansible.com/ansible/latest/user_guide/command_line_tools.html)

## Ansible utilities

### ansible

```bash
# display version
ansible --version
```

→ [docs.ansible.com](https://docs.ansible.com/ansible/latest/cli/ansible.html)

### ansible-config

### ansible-console

### ansible-doc

```doc
# displays the list of available plugins
ansible-doc -t inventory -l

# displays plugin-specific documentation and examples
ansible-doc -t inventory <plugin name>
```

### ansible-galaxy

```bash
# display version
ansible-galaxy --version
```

→ [docs.ansible.com](https://docs.ansible.com/ansible/latest/cli/ansible-galaxy.html)

### ansible-inventory

```bash
# display version
ansible-inventory --version
```

→ [docs.ansible.com](https://docs.ansible.com/ansible/latest/cli/ansible-inventory.html)

### ansible-playbook

```bash
ansible-playbook
```

## ansible-pull

## ansible-vault

## Additional tools

### ansible-lint

```bash
ansible-lint verify-apache.yml
```

→ [docs.ansible.com](https://ansible-lint.readthedocs.io/en/latest/)
