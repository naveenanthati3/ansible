Generate SSH Keys on the Master
 <!-- ssh-keygen -t rsa -b 4096 -->

Exchange SSH Keys by ssh-copy-id command
 <!-- ssh-copy-id -i ~/.ssh/id_rsa.pub slave1@x.x.x.x -->
 <!-- ssh-copy-id -i ~/.ssh/id_rsa.pub slave2@x.x.x.x -->
 <!-- ssh-copy-id -i ~/.ssh/id_rsa.pub slave3@x.x.x.x -->

Slaves are created in AWS with key 

Add Hosts in Inventory file
<!-- x.x.x.x ansible_user=ubuntu ansible_ssh_private_key_file=/home/ubuntu/srs_tasks.pem
x.x.x.x ansible_user=ubuntu ansible_ssh_private_key_file=/home/ubuntu/srs_tasks.pem
x.x.x.x ansible_user=ubuntu ansible_ssh_private_key_file=/home/ubuntu/srs_tasks.pem -->
1
Check all nodes are alive
<!-- ansible -m ping all -->

A Role "webserver" is used to install NGINX server on slaves based on type of OS Distribution.
From Ansible facts type of distro yml file picked by ansible (ex. Debian = debian.yml)

To Install webservers on Slaves
<!-- ansible-playbook -i srs_task_inventory.ini main.yml -->

To Remove Webservers on Slaves
<!-- ansible-playbook -i srs_task_inventory.ini remove.yml -->