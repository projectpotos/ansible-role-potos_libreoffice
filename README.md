
# Ansible Role - potos_libreoffice

Install and configure LibreOffice.

[![Test](https://github.com/projectpotos/ansible-role-potos_libreoffice/actions/workflows/test.yml/badge.svg)](https://github.com/projectpotos/ansible-role-potos_libreoffice/actions/workflows/test.yml)

## Example Playbook

As this role is tested via Molecule one can use [that playbook](./molecule/default/converge.yml) as a starting point:

```yaml
---

- name: Converge
  hosts: all
  gather_facts: yes

  tasks:
    - name: run role
      ansible.builtin.include_role:
        name: ansible-role-potos_libreoffice
      vars:
        potos_libreoffice_templates:
          - source: "https://extensions.libreoffice.org/assets/downloads/1011/1677853134/CV-deux-colonnes-sobre-v2.ott"
          - name: squares.ott
            source: "https://extensions.libreoffice.org/assets/downloads/z/1cm-paper.ott"
            destination_directory: sales
        potos_libreoffice_fonts:
          # Ubuntu does not have a package for these fonts.
          # - name: adobe-source-sans-pro-fonts
          - source: "https://github.com/adobe-fonts/source-sans/raw/release/TTF/SourceSans3-Regular.ttf"
            family: source-sans
```

## Role Variables

The default variables are defined in [defaults/main.yml](./defaults/main.yml):

```yaml
---

# List fonts that you want to install. These are packages containing the fonts.
#
# Explanation of items in the list:
# Either specify `name` or specify `url`.
# name: (optional) The name of the package to install
# source: (optional) The URL to the font, a `ttf` file.
# family: (optional when `source` is specified) A name to store the fonts in.
# potos_libreoffice_fonts:
#   - name: adobe-source-sans-pro-fonts
#   - source: https://github.com/adobe-fonts/source-sans/blob/release/TTF/SourceSans3-Regular.ttf
#     family: source-sans
potos_libreoffice_fonts: []

# List of templates that you want to install.
#
# Explanation of items in the list:
# source: (required) The URL to the template.
# name: (optional) The name to call the file.
# destination_directory: (optional) The directory to put the file in. This is relative to the path where LibreOffice expects templates to be.
#
# potos_libreoffice_templates:
#   - souce: "https://cloud.adfinis.com/remote.php/webdav/syintern/some/path/my_company_template.odt"
#   - name: my_template.odt
#     souce: "https://cloud.adfinis.com/remote.php/webdav/syintern/some/path/my_sales/template.odt"
#     destination_directory: sales
potos_libreoffice_templates: []
```

Another option is to use `ansible-doc` to read the argument specification:

```sh
`ansible-doc --type role -r . main ansible-role-potos_libreoffice`
```

## Requirements

N/A

## License

See [LICENSE](./LICENSE)

## Author Information

[Project Potos](https://github.com/projectpotos)
