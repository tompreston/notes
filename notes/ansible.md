# Ansible
Setup hosts (infrastructure) by editing:

	/etc/ansible/hosts

Run ad-hoc commands (modules `-m`, args `-a`):

	ansible all -m ping
	ansible all -a '/usr/bin/echo hello world'

Instally roles:

	ansible-galaxy install geerlingguy.docker

Create playbooks, which use roles, to configure infrastructure. See the example
playbooks.

Gather facts:

    ansible all -m ansible.builtin.setup

https://docs.ansible.com/ansible/latest/collections/ansible/builtin/setup_module.html
