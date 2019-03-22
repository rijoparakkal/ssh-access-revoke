# ssh-access-revoke
Assume that we have Ansible master-Agent setup across all servers. 

### For example we have 2 servers 
1. host1
2. host2

##  Creating one user across all servers

Type this command in terminal
#### ansible-playbook add_user.yml
``` ---
- hosts: host1,host2
  become: true
  tasks:
   - name: Create a login user
     user:
      name: developer_name
      password: 'passowrd'
      groups: # Empty by default, here we give it some groups
      - sudo
      state: present
      shell: /bin/bash       # Defaults to /bin/bash
      system: no             # Defaults to no
      createhome: yes        # Defaults to yes
      home: /home/developer_name  # Defaults to /home/<username>
```  
