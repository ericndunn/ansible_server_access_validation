ASSUMPTIONS:
All ssh keys copied to servers in inventory file.
Ansible Installed
Repo git cloned to local (/path/to/ansible_server_access_validation)

Create "/path/to/file/inventory" file and edit with the server list you want to verify access.

See https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html

cd to /path/to/ansible_server_access_validation

run the following command line (IF using inventory groups):

ansible-playbook -i /path/to/file/inventory -l GROUP_NAME1 /path/to/ansible_server_access_validation/server_access_status.yml -e "jenkins_ws=/path/to/output build_id=123" --ask-pass

run the following command line (IF NOT using inventory groups):

ansible-playbook -i /path/to/file/inventory /path/to/ansible_server_access_validation/server_access_status.yml -e "jenkins_ws=/path/to/output build_id=123" --ask-pass

NOTE:  Use "--ask-pass" parameter to be prompted for ssh key password.  
       IF no key password was configured, do not use "--ask-pass"



