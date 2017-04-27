<h2>Example Plays / Playbooks</h2>

Playbooks are stored in YAML format

Execution of playbook:

`$ ansible-playbook playbook.yml`

Example play:

```
---
- hosts: webservers
  remote_user: root
  tasks:
  - name: Install Apache
    yum: name=httpd state=present
  - name: Start Apache
    service: name=httpd state=started
```

Play Declarations:

```
---
- hosts: webservers
  vars:
    git_repo: https://github.com/repo.git
    http_port: 8080
    db_name: wordpress
  sudo: yes
  sudo_user: wordpress_user
  gather_facts: no
```
Example playbook from Pluralsight

```
---
- hosts: webservers
  sudo: yes
  gather_facts: no

  tasks:
  - name: Install Apache
    yum: name=httpd state=present

  - name: Start Apache
    service: name=httpd enabled=yes state=started

- hosts: dbservers
  sudo: yes
  gather_facts: no

  tasks:
  - name: Install MySQL
    yum: name=mysql-server state=present

  - name: Start MySQL
    service: name=mysqld state=started

- hosts: webservers:dbservers
  sudo: yes
  gather_facts: no

  tasks:
  - name: Stop IPTABLES
    service: name=iptables state=stopped
```

Include playbooks/variables on other playbook

```
tasks:
  - include: wordpress.yml
    vars: 
      sitename: Wordpress Blog
  - include: loadbalancer.yml
  - include_vars: variables.yml
```

