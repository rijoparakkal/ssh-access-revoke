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
      password: 'password'
      groups: # Empty by default, here we give it some groups
      - sudo
      state: present
      shell: /bin/bash       # Defaults to /bin/bash
      system: no             # Defaults to no
      createhome: yes        # Defaults to yes
      home: /home/developer_name  # Defaults to /home/<username>
```  
Above command will create one user in all 2 servers. We can change the username and password in yml file

##  Removing the user from all servers

Type this command in terminal
#### ansible-playbook add_user.yml
``` ---
- hosts: host1,host2
  become: true
  tasks:
   - name: ansible remove user
     user:
      name: developer_name
       state: absent
     
```  
Above command will remove the mentioned user from all servers
