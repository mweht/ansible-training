<h2>Example Play / Playbook</h2>

Playbooks are stored in YAML format

```---
- hosts: webservers
  remote_user: root
  tasks:
  - name: Install Apache
    yum: name=httpd state=present
  - name: Start Apache
    service: name=httpd state=started```
