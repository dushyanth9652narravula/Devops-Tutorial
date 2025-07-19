# Server Configuration Using Vagrant

## Introduction

- As we know vagrant is used to provision the virtual machines automatically by using simple commands such as `vagrant init <boxname>`, `vagrant up`, `vagrant destroy` etc. But all these virtual machines created by vagrant are configured by a single file called `Vagrantfile`.

- Inorder to configure the VM as we required, we need to understand the code inside the Vagrantfile. We can configure the resources required for VM to run such as RAM, ROM, CPUs , Networking etc.

- Vagrantfile is written in Ruby Language. We doesn't need to learn Ruby Programming Language to understand the vagrant file. Vagrantfile starts with a simple syntax which is `Vagrant.configure('2') do |config|`. `Vagrant.configure('2')` represents that it is using the vagrant version 2 which is a stable version of vagrant. The `config` in between the pipe symbol is just an class object. Here we can name anything we want but we need to use the same object in all the code.

## Configuring the IP, RAM, CPUs of Virtual Machine

- After `Vagrant.Configure` the first thing we actually need to configure is what operating system we are using. If we are using linux what box we are using from vagrant cloud. To set up the Os or box we use `config.vm.box` syntax. For example if i want to use `ubuntu/focal64` then my syntax is `config.vm.box = ubuntu/focal64`.

- Generally we have two types of networking. One is Private IP address through which we can access the Virtual Machine by using host machine only. This Private IP address is used to test whether webserver in the virtual machine is running correctly or not. To set up the Private IP Address for the Virutal Machine we use `config.vm.network "private_network", ip : <ip_address>`. But while setting up th IP Address don't change 1st and 2nd octant, change only 3rd and 4th octant. In `192.168.33.10`, `33` and `10` are 3rd and 4th quadrants. 

- Second Networking is `public network` we creates a bridged network, so that we can access the VM from our devices such as Phone etc but both VM and your phone connected on same LAN. Here Ip address is dynamic which is assigned by the Router (Here we get IP address similar to we get ip address when we deploy streamlit app locally etc). So to enable this public network we use `config.vm.nextwork "public_network"`.

- To configure CPU, RAM then we actually need to configure the virtual machine provider. If we are using Windows OS, we actually use VirutalBox as VM provider. If we are using MAC, we use VMWare as VM provider. To configure VM Provider, we use `config.vm.provider "<VM Provider>" do |<Any object name>|`. For example `config.vm.provider "virtualbox" do |vb|`. Under this we can use `vb.memory` to configure the RAM and `vb.cpus` to configure cpus etc.