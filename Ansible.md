### 

### iteration
```
      - name: create account
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