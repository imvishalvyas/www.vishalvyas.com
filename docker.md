Ansible is a automation tool which is widely used, you can install and install, configure and manage number of system and services remotely. you can install software and manage services and tasks without needing manually log in to each servers. you have to install ansible in one machine and use ssh to communicate host each other.


Ansible uses Playbooks which is written in YAML format. it's uses module base format. with playbook can run multiple tasks at time and provide more advance functionality, YAML file always start with "---" syntax.

### In this article we will see how to install and configure apahce2 using ansible YAML script.

Master server : 10.80.253.11 [Ansible server, ]
Slave 1           : 10.80.253.12 [need to install apache2 in slave 1]
Slave 2           : 10.80.253.13 [need to install apache2 in slave 2]

We need to configure slave server info in our ansible configuration file, click here to know how to add client machine to ansible.

Let's update our apache2.yml file and install apche on both slave servers. add below lines in YAML file and save.
```
$ vim apache2.yml
```
```
---
- hosts: servers  #server host or group name 
  sudo: yes
  tasks:
    - name: install apache2
      apt: name=apache2 update_cache=yes state=latest

    - name: enabled mod_rewrite
      apache2_module: name=rewrite state=present
      notify:
        - restart apache2

  handlers:
    - name: restart apache2
      service: name=apache2 state=restarted
```

`Syntex` : 
-hosts : it's our server group name 
-name : define name of package need to be installed.

Now let's run our playbook, it will install apache2 on both the servers.
```
$ansible-playbook apache.yml
```
```
PLAY [servers] ********************************************************************************

TASK [Gathering Facts] ************************************************************************
ok: [slave2]
ok: [slave1]

TASK [install apache2] ************************************************************************
changed: [slave1]
changed: [slave2]

TASK [enabled mod_rewrite] ********************************************************************
changed: [slave1]
changed: [slave2]

RUNNING HANDLER [restart apache2] *************************************************************
changed: [slave2]
changed: [slave1]

PLAY RECAP ************************************************************************************
slave1                     : ok=4    changed=3    unreachable=0    failed=0
slave2                     : ok=4    changed=3    unreachable=0    failed=0
```

That's it, apahce2 is now installed on both slave serves. there is no failed messages. you can verify it using slave server ip address in web browser.



So we have installed apache only on servers using ansible playbooks, in the next article i will explain you to how to deploy static website with images using ansible playbook. Keep reading and share our posts.

thanks,
Vishal Vyas
