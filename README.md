# Ansible Role - potos_libreoffice

Role to use as template for new roles of Potos Linux Clients.

[![Test](https://github.com/projectpotos/ansible-role-potos_libreoffice/actions/workflows/test.yml/badge.svg)](https://github.com/projectpotos/ansible-role-potos_libreoffice/actions/workflows/test.yml)

## Example Playbook

As this role is tested via Molecule one can use [that playbook](./molecule/default/converge.yml) as a starting point:

```yaml
---

- name: Converge
  hosts: all
  gather_facts: yes

  roles:
    - ansible-role-potos_libreoffice
```

## Role Variables

The default variables are defined in [defaults/main.yml](./defaults/main.yml):

```yaml
---

# List fonts that you want to install. These are packages containing the fonts.
potos_libreoffice_fonts: []

# List of templates that you want to install.
potos_libreoffice_templates: []
```

Another option is to use `ansible-doc` to read the argument specification:

```sh
ansible-doc --type role -r . main ansible-role-potos_libreoffice
```

## Requirements

N/A

## License

See [LICENSE](./LICENSE)

## Author Information

[Project Potos](https://github.com/projectpotos)
