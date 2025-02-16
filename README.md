PASSWORDLESS AUTHENTICATION:
For passwordless authentication we need to copy local server public key to enhance the passwordless authentication 
"ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>" 
this copies the public key and we can login without private key 

Setting up vault:
"openssl rand -base64 2048 > vault.pass"  we can randomly generate vault password with encryption 
then we need to create a vault file named pass.yml "ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass"
next we can enter out sensitive credentials inside of pass.yml and if we need to edit we can use "ansible-vault edit group_vars/all/pass.yml --vault-password-file vault.pass"
when we enter it and written playbook we need to use it as "ansible-playbook EC2.yml --vault-password-file vault.pass" this could authenticate the file and ensure the datas are configure in the mentioned resource.



