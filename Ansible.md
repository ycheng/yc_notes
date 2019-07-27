### Roles
```- host: xxx
  roles:
    - db
    - { role:ruby, sudo_user:$user }
    - web

# Uses:
# roles/db/tasks/*.yml
# roles/db/handlers/*.yml
```

### Vars
* Env Vars
```vars:
  local_home: "{{ lookup('env','HOME') }}"
```
* Vars can block task
```tasks:
    - name: Create the SSH directory.
      file: state=directory path=${project_root}/home/.ssh/
      only_if: "$vm == 0"
```

### Handles
* Multiple tasks can notify the same handlers. The handles will be run in the end once only if it's notified)
```tasks:
  - name: install apache
    action: apt pkg=apache2 state=latest
    notify:
      - start apache2

handlers:
  - name: start apache2
    action: service name=apache2 state=started```

### Iteration
```      - name: create account
        become: True
        user:
          name: "{{ item }}"
          groups: user_group_name
        with_items:
          - user1
          - user2
```

### Enable remote python session use local ssh-agent key.
* ansible.cfg
* [ssh_connection]
* ssh_args = -o ForwardAgent=yes -o ControlMaster=auto -o ControlPersist=60s

### install in ubuntu
* $ sudo apt update
* $ sudo apt install software-properties-common
* $ sudo apt-add-repository --yes --update ppa:ansible/ansible
* $ sudo apt install ansible