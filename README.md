# Elixir provisioning for Vagrant

## What is it for?

Developers can use a Virtual Machine (VM) for development in order to quickly get up and running with a system that has Elixir installed. Everyone will have the same setup regardless of the host machine.

The VM will have:
* Linux (Ubuntu)
* Erlang
* Elixir
* PostgreSQL
* nodejs 6 and other dependencies for the Phoenix framework

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

## Phoenix / inotify auto-reload issues

Warning: There are issues with Phoenix auto reloading and Vagrant. This appears to be because
of inotify being incompatible with the `/vagrant` directory being connected to the host file system.

Vagrant can still be used for instance for doing releases of a Phoenix project.

## Warning: Hex dependencies

If you do `mix deps.get` on the vagrant machine it will get dependencies appropriate for that.
Some dependencies are only compatible for that machine. This means that if you run `mix deps.get`
on the vagrant machine you can only use those kinds of dependencies on the vagrant machine and not
on the host. And vice versa.
