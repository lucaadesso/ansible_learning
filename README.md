# create roles for two different type of servers
# main task will be created in 
# roles/SERVER_TYPE/tasks/main.yml

ansible-galaxy init roles/webserver
ansible-galaxy init roles/dbserver

# rekey will change the default crypting key for the become_vault.yml file
# initial password is 123456
 
ansible-vault rekey become_vault.yml
Vault password:
New Vault password:
Confirm New Vault password:

# edit is used to change the sudo password for the servers
ansible-vault edit become_vault.yml
Vault password:

# This is the real execution of the ansible playbook. It ask the vault password to decrypt variables that are eventually used inside the playbook.
ansible-playbook -i inventory secure.yml --ask-vault-password
ansible-playbook -i inventory update.yml --ask-vault-password

