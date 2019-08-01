ASSUMPTIONS:
All ssh keys copied to servers in inventory file.
Ansible Installed
Repo git cloned to local (/path/to/ansible_server_access_validation)

1.  Create "/path/to/file/inventory" file and edit with the server list you want to verify access.
-----------------
'
[GROUP_NAME1]
server1
server2

[GROUP_NAME2]
server3
server4
'
-----------------

2.  cd to /path/to/ansible_server_access_validation

3.  run the following command line:

>ansible-playbook -i /path/to/file/inventory -l GROUP_NAME1 /path/to/ansible_server_access_validation/server_access_status.yml -e "jenkins_ws=/path/to/output build_id=000" --ask-pass

NOTE:  Use "--ask-pass" parameter to be prompted for ssh key password.  
       IF no key password was configured, do not use "--ask-pass"



