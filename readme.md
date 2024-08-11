Steps to use:

1) Use ansible_controller and ansible_client packer files in "Packer-Files-Repo" to spin up controller and client machines.

2) In controller, set the following options

    - cd /etc/ansible
    - mv ansible.cfg ansible.cfg.old
    - ansible-config init --disabled > ansible.cfg
    - cat ansible.cfg

3) In config file, change the following options (uncomment them by removing ;):
    * set host_key_checking to False
    * set private_key_file path as /etc/ansible/ansibleadmin.pem
    * just uncomm private_role_vars
    * set remote_port as 22
    * set remote_user as ansibleadmin

4) Outside of config file, copy the ritiskk2.pem file to /etc/ansible/ansibleadmin.pem

5) Now in the dir to work with ansible, create inventory file

    Eg:
    [clients]
    client1 ansible_host=<pip of client>

    [controller]
    controller ansible_host=<pip of controller>

6) Test connection with:
    - ansible -i inventory all -m ping 