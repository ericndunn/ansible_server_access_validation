**ASSUMPTIONS:**

 - All ssh keys copied to servers in inventory file.
 - Ansible Installed
 - Repo git cloned to local (/path/to/ansible_server_access_validation)

**NOTE:**

In ansible There is no option to store passphrase-protected private key.
For that we need to add the passphrase-protected private key in the ssh-agent.
Start the ssh-agent in the background.

    eval "$(ssh-agent -s)"

Add SSH private key to the ssh-agent

    ssh-add ~/.ssh/id_rsa

Now try running ansible-playbook and ssh to the hosts.

**Reference:**
https://stackoverflow.com/questions/50277495/how-to-run-an-ansible-playbook-with-a-passphrase-protected-ssh-private-key

 - Create "/path/to/ansible_server_access_validation/inventory" file
       and edit with the server list you want to verify access.

See https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html

 - cd to /path/to/ansible_server_access_validation
	 - run the following command line (IF using inventory groups):
 `ansible-playbook -i inventory -l GROUP_NAME server_access_status.yml`

	 - run the following command line (IF NOT using inventory groups):
`ansible-playbook -i inventory -l GROUP_NAME server_access_status.yml`
