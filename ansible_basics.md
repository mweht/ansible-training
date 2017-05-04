# ansible-training
<h2>Useful Ansible commands</h2>

List modules with a brief description

`ansible-doc -l`

---

Show module information

`ansible-doc <module_name>`

---

Show module playbook examples

`ansible-doc -s <module_name>`

---

Login to a box

`ansible ssh <server_name>`

---

Example command

`ansible <all/group/host> -i <path_to_inventory_file> -u <user> -m <module> -a "<parameter>" -k --sudo`

`ansible all -i inventory -u vagrant -m command -a "uptime" -k`

---

Dump all infrastructure data to a text file under a folder

`ansible all -i <inventory_file> -m setup --tree ./folder`

---

Stop IPTables service

`ansible webservers:dbservers -i inventory_file -m service -a "name=iptables state=stopped" --sudo`

---

Start mysqld service

`ansible dbservers -i inventory_file -m service -a "name=mysqld enabled=yes state=started" --sudo`

---

Install something with YUM

`ansible dbservers -i inventory_file -m yum -a "name=mysql-server state=present" --sudo`

---
