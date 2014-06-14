# LAMP (PHP 5.5) w/ Vagrant

A basic Ubuntu 12.04 Vagrant setup with PHP 5.5.

Based on [https://github.com/bryannielsen/Laravel4-Vagrant](https://github.com/bryannielsen/Laravel4-Vagrant)

## Requirements

* VirtualBox - Free virtualization software [Download Virtualbox](https://www.virtualbox.org/wiki/Downloads)
* Vagrant **1.3+** - Tool for working with virtualbox images [Download Vagrant](https://www.vagrantup.com)
* Git - Source Control Management [Download Git](http://git-scm.com/downloads)

## Setup


* run `vagrant up` inside the newly created directory
* (the first time you run vagrant it will need to fetch the virtual box image which is ~300mb so depending on your download speed this could take some time)
* Vagrant will then use puppet to provision the base virtual box with our LAMP stack (this could take a few minutes)
* You can verify that everything was successful by opening http://vagrant.dev in a browser

## Usage

Some basic information on interacting with the vagrant box

### Port Forwards

* 8080 - Apache
* 33306 - MySQL 


### Default MySQL Database

* User: root
* Password: (blank)


### PHPmyAdmin

Accessible at http://vagrant.dev/phpmyadmin using MySQL access credentials above.

### PHP XDebug

_Note: All XDebug settings can be configured in the php.ini template at `puppet/modules/php/templates/php.ini.erb`_


### Vagrant

Vagrant is [very well documented](http://vagrantup.com/v1/docs/index.html) but here are a few common commands:

* `vagrant up` starts the virtual machine and provisions it
* `vagrant suspend` will essentially put the machine to 'sleep' with `vagrant resume` waking it back up
* `vagrant halt` attempts a graceful shutdown of the machine and will need to be brought back with `vagrant up`
* `vagrant ssh` gives you shell access to the virtual machine

----
##### Virtual Machine Specifications #####

* OS     - Ubuntu 12.04
* Apache - 2.4.6
* PHP    - 5.5.4
* MySQL  - 5.5.32
* Memcached - 1.4.13
