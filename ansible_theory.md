In earlier days,System admin used to manage-
-10 linux
-5 windows and other servers and they would have to ssh into each machine and update individually(packages,services)
Now configuration management treats it as IAC and can configure things on machines together and all at once
#Ansible
-Ansible is the most important config management system and uses **python** and **YAML** 
-It uses push model 
Laptop/Control Node
        ↓
Push configs
        ↓
Server1 Server2 Server3
-It is agentless-does not require agents on every machine like puppet.Can scale up and down easily because of this.
-Example playbook-
hosts: webservers
  become: yes

  tasks:
    - name: Install nginx
      apt:
        name: nginx
        state: present
      
-**Dynamic inventory**-Ansible fetches information publically from cloud servers
basically, Ansible asks AWS → "Give me all EC2 instances with tag=webserver"

#Puppet
-This uses pull mechanism and is old version
Server1 ----\
Server2 ----- > Puppet Server
Server3 ----/
-Agents contact the server
