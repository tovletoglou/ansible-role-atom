# Ansible Role: Atom

Install (Atom](<https://www.atom.io/>) from rpm.

## Requirements

- Ansible >= 2.2
- Fedora 25
- sudo

The role may run on other systems, but it is not tested.

## Role Variables

Add action "Open with Atom" to Nemo (true | false).

```
atom_add_action: false
```

Nemo action template.

```
atom_action_template: templates/atom.nemo_action.j2
```

User list that will deploy the Nemo action "Open with Atom". The default will get the ansible user.

```
atom_users:
  - {
      name: "{{ ansible_user_id }}",
      home: "{{ ansible_user_dir }}",
      conf: "",
    }
```

## Example

```
- hosts: all
  roles:
    - ansible-role-atom
```

In the next example I use custom vars to:
- deploy the Nemo action
- define a user list
- link the firs user's Atom configuration to another directory to make it portable

```
- hosts: all
  roles:
    - ansible-role-atom
  vars:
    atom_add_action: true
    atom_users:
      - {
          name: USER_NAME,
          home: /home/USER_NAME,
          conf: /home/USER_NAME/Dropbox/software/.atom/,
        }
      - {
          name: root,
          home: /root,
          conf: "",
        }
```

## Dependencies

None

## License

MIT

## Author Information

Apostolos Tovletoglou [ansible-role-atom](https://github.com/tovletoglou/ansible-role-atom)
