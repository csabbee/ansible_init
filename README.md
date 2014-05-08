# Ansible usage

## target:

	sudo apt-get update
	sudo apt-get install openssh-server
	sudo ufw allow 22

[askubuntu](http://askubuntu.com/questions/51925/how-do-i-configure-a-new-ubuntu-installation-to-accept-ssh-connections)

That's the very minimum. It allows unlimited failed password attempts on a known port. Direct root-login is disabled (you can still su and sudo once logged in). If your username and password are guessable and the Internet can see the server, somebody will eventually break in.

You want to harden it from the standard setup. There are [several suggestions here](http://askubuntu.com/questions/2271/how-to-harden-an-ssh-server) but at the least, I suggest:

    Use key-based logins. Disable password logins.
    Move it off port 22. Use something crazy-high, in the 20000-60000 range.
    Use fail2ban to ban people who do find it and try to brute it.

They take about 10 minutes in total and you go from a 1/10000 chance of being broken in to a probability so small, there isn't enough paper in the world to write its fraction... Assuming you're careful with your key, it has a password of its own and you don't trumpet your credentials all over the net.

If the computer is behind a router, you'll also want to do some port forwarding. This is router-specific so I'll just direct you to http://portforward.com


#### Auth log is located here: /var/log/auth.log


## local:

	sudo apt-get update
	sudo apt-get install python-pip python-dev git -y
	sudo pip install PyYAML jijna2 paramiko
	git clone https://github.com/ansible/ansible.git
	cd ansible
	sudo make install
	sudo mkdir /etc/ansible
	sudo cp ~/ansible/examples/hosts /etc/ansible/


#### Ansible config

create an ansible.cfg in /etc/ansible directory

enable logging:
	[defaults] 
	log_path=/path/to/logfile

### ping host(s)

	ansible -m ping -i /etc/ansible/hosts all -k

### Useful sites

[OpenSSH Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
