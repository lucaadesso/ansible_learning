# Create roles for two different type of servers
### The yaml file that perform the tasks is usually roles/SERVER_TYPE/tasks/main.yml

ansible-galaxy init roles/webserver
ansible-galaxy init roles/dbserver

# Change the crypto key
### "rekey" is the option to change the key defined to encrypt the file become_vault.yml
# Change the crypto key
### Initial password set to 123456

ansible-vault rekey become_vault.yml
Vault password:
New Vault password:
Confirm New Vault password:

# Change the sudo password or any other variables hidden in a yaml file
### "edit" is the option to change the yaml file specified

ansible-vault edit become_vault.yml
Vault password:

# Execute the ansible playbook
### This is the main execution of the ansible playbook. It will ask the vault password to decrypt the variable used in the playbook.

ansible-playbook -i inventory secure.yml --ask-vault-password
ansible-playbook -i inventory update.yml --ask-vault-password
