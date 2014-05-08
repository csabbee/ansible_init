# Ansible usage

## target:

	sudo apt-get update
	sudo apt-get install openssh-server
	sudo ufw allow 22


## local:

	sudo apt-get update
	sudo apt-get install python-pip python-dev git -y
	sudo pip install PyYAML jijna2 paramiko
	git clone https://github.com/ansible/ansible.git
	cd ansible
	sudo make install
	sudo mkdir /etc/ansible
	sudo cp ~/ansible/examples/hosts /etc/ansible/

