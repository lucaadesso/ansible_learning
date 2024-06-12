# Creare ruoli per due tipi diversi di server
### Il task principale sarà creato in roles/SERVER_TYPE/tasks/main.yml

ansible-galaxy init roles/webserver
ansible-galaxy init roles/dbserver

# Cambiare la chiave di crittografia
### "rekey" cambierà la chiave di crittografia predefinita per il file become_vault.yml
### La password iniziale è 123456

ansible-vault rekey become_vault.yml
Vault password:
New Vault password:
Confirm New Vault password:

# Cambiare la password sudo o qualsiasi variabile nascosta in un file yaml
### "edit" viene utilizzato per cambiare la password sudo per i server

ansible-vault edit become_vault.yml
Vault password:

# Eseguire il playbook ansible
### Questa è l'esecuzione reale del playbook ansible. Chiederà la password del vault per decriptare le variabili che eventualmente vengono utilizzate all'interno del playbook.

ansible-playbook -i inventory secure.yml --ask-vault-password
ansible-playbook -i inventory update.yml --ask-vault-password
