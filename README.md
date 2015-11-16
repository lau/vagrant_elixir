# Elixir provisioning for Vagrant

## What is it for?

Developers can use a Virtual Machine (VM) for development in order to quickly get up and running with a system that has Elixir installed. Everyone will have the same setup regardless of the host machine.

The VM will have:
* Linux (Ubuntu)
* Erlang
* Elixir
* PostgreSQL
* various dependencies for the Phoenix framework

The provisioning script can easiliy be modified for other versions of the software.

If a Phoenix project is detected during the first `vagrant up`, the database will also be set up and seeded.

## Prerequisites

* Install Vagrant ( https://www.vagrantup.com/ )
* Install VirtualBox ( https://www.virtualbox.org/ ) or alternatively VMWare.

## How to use it

1. Add the two files `Vagrantfile` and `vagrant_provision.sh` to any directory. With an Elixir project in it or not.
2. Run `vagrant up` This will take a while the first time as it will install Erlang, Elixir, PostgreSQL and more.
3. SSH into the vagrant box with `vagrant ssh`.

The `/vagrant` directory will be linked to the project directory on the host machine.

## Version control

 `Vagrantfile` and `vagrant_provision.sh` should be added to version control.
On the other hand it is recommended to ignore the `.vagrant` directory. If you are using git you could add this line to `.gitignore`:
`.vagrant/*`
