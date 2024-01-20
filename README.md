# Ansible Role: Bash_aliases

Configuration of Bash aliases for multiple users on Debian/Ubuntu.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):


    bash_aliases_setup: true

Whether or not to set up bash aliases.


    bash_aliases_per_user: false

Whether set up bash aliases per user.

false - Configure identical aliases from bash_aliases_list for all users specified in bash_aliases_users.

true - Configure aliases per user from bash_aliases_per_user_list.


    bash_aliases_path: "~/.bash_aliases"

The path to the .bash_aliases file in the system.


    bash_aliases_users:
      - root

List of users for alias configuration. Used when bash_aliases_per_user: false.


    bash_aliases_list:
      - {alias: 'h', command: 'history'}

Dictionary structure holding a list of aliases. Used when bash_aliases_per_user: false.


    bash_aliases_per_user_list:
      - {user: 'root', alias: 'h', command: 'history'}

Dictionary structure holding a list of aliases per user. Used when bash_aliases_per_user: true.

## Dependencies

None.

## Example Playbook

    - hosts: server
      vars:
        - bash_aliases_setup: true
        - bash_aliases_per_user: false
        - bash_aliases_users:
          - vagrant
          - root
        - bash_aliases_list:
          - {alias: 'h', command: 'history'}
          - {alias: 'cdlog', command: 'cd /var/log'}
      roles:
        - { role: raf-net.bash_aliases }

---

    - hosts: server
      vars:
        bash_aliases_setup: true
        bash_aliases_per_user: true
        bash_aliases_per_user_list:
          - {user: 'root', alias: 'h', command: 'history'}
          - {user: 'vagrant', alias: 'c', command: 'clear'}
          - {user: 'vagrant', alias: 'cdlog', command: 'cd /var/log'}
      roles:
        - { role: raf-net.bash_aliases }


## License

MIT / BSD

## Author Information

Raf-Net
