# Vagrant
Use vagrant to manage virtual machines from the command line.
For example:

	vagrant/libvirt-debian/Vagrantfile.

From https://app.vagrantup.com/debian/boxes/buster64
You need to get NFS working for file syncing, so get that first. I've just
disabled it for now.

Commands:

	vagrant init debian/buster64
	vagrant up
	vagrant destroy
	vagrant ssh
	vagrant ssh-config

