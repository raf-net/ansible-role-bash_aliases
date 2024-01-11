# Ansible Role: Bash_aliases

Configuration of Bash aliases for multiple users on Debian/Ubuntu.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):


    bash_aliases_setup: false

Whether or not to set up bash aliases


    bash_aliases_path: "~/.bash_aliases"

The path to the .bash_aliases file in the system.


    bash_aliases_users:
      - root

List of users for alias configuration.


    bash_aliases_list:
      - {alias: 'h', command: 'history'}  # Quick history list overview.

Dictionary structure holding a list of aliases.


## Dependencies

None.

## Example Playbook

    - hosts: server
      roles:
        - { role: raf-net.bash_aliases }

## License

MIT / BSD

## Author Information

Raf-Net
