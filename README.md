# Ansible-Docker-Web-Server-Setup

Write an Ansible PlayBook that does the following operations in the managed nodes:
* Configure Docker
* Start and enable Docker services
* Pull the httpd server image from the Docker Hub
* Run the docker container and expose it to the public
* Copy the html code in the/var/www/html directory and start the web server

Step 1: Launch two Amazon Linux 2 instances, one for the master and the other for the slave.

Step 2: Install Ansible version `2.9.23-1.amzn2.noarch`.

Step 3: Install the Ansible Collection: `ansible-galaxy collection install community-docker`.

Step 4: Create a `conf_ansible.cfg` file for configuring Ansible in the Ansible folder.

Step 5: Create an inventory file and add the IP address of the slave instance under the `[dev]` group.

Step 6: Check the connectivity to the slave node using the following command:
        ```ansible dev -m ping```
        If you encounter an error, go to the slave node and edit the SSH configuration file: 
        ```vim /etc/ssh/sshd_config```
        Uncomment the line #PasswordAuthentication yes, save the file, and restart SSH on the slave node. Then, from the managed node, copy the SSH key to the slave node using the command:
        ```ssh-copy-id @ec2-user```
        Replace @ec2-user with the slave node's IP address.

Step 7: Create a file named Docker.yml and paste the entire Ansible playbook code into it.

Step 8: Run the Ansible playbook using the following command:
        ```ansible-playbook Docker.yml```

Step 9: To check if the web server is running successfully on the slave node, copy the slave's IP address and access it using a web browser with the following format:
        ```http://slave-ip:8080/index.html```
        Replace slave-ip with the actual IP address of the slave node.


These steps should help you set up a master-slave configuration and deploy a web server using Ansible.
        
