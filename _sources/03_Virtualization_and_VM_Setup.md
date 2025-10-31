# Virtualization and VM Setup

## Virtualization

- Virtualization is a technology which creates virtual representations of the servers, storages, networks and other physical machines. It simulates the computing environment by dividing the physical resources into virtual machines, operating systems and other components.

- The Traditional Way of doing businees is having one server for one application. Suppose consider the following example .

  **Ex**

  1. Consider a business runs three servers where first server is for email application which uses windows operating system, second server is for web application which uses linux operating system and 3rd server for database which uses Unix Operating System.

  2. Instead of running three applications in three different servers, what if we can able to run all three applications in server even isolating each application with respective operating system so that we can reduce the cost of buying more servers. This is what Virtualization does.

  3. Virtualization basically divides the physical components of the server into virtual machines where each virtual machine runs different operating system having different applications such as email, web, databse etc.

- The Software that enables virtualization is called **Hypervisor**. It actually allocates the system resources such as Storage, RAM, CPU etc to each virtual machine.

- We have two types Hypervisors . One is Type - I and second one is Type - II

  **Type - I** : Type - I hypervisors are simply installed on top of bare metal. Bare metal means there is no existing operating system on top of physical resources such RAM, ROM and MotherBoard. So there is no operating system in between Hypervisor and Physical components. These type of Hypervisors are used in production level only.

  **Ex** : VMware ESXI, Critix XenServer, Microsoft Hyper - V

  **Type - II** : Type - II Hypervisors are installed on top of existing operating systems. That means there is an operating system in between Hypervisor and Physical Components of the system. These type of hypervisors are used for personal usecase to test new softwares or run differnt operating system in single system.

  **Ex** : Oracle Virtual Box, Microsoft Virtual PC, VMware Workstation.

- There are actually so many benifits of virtualiation technology. Those are:

  1. It saves money on hardware and power consumption. If we use virtualization technology, we doesn't need too many servers which automatically reduces the cost of buying servers and since we use few no of servers it also decreases the powe consumption.

  2. It also reduces the money invested on floor space. Since virtualization reduces the usage of more servers so it automatically reduces the usage of floor space.

  3. Similary it also reduces the money for maintainance and management of the servers as we require system admininstrators to maintain the health of the servers.

  4. Virtual Machines are portable. Since these are just software files, so we can easily transfer them from one machine to another machine.

  5. Through virtualization technology, we can use complete resources of the server which gives full computing capability.

  6. Virtualization easily resuces the servers from disasters. Since VM are software files we can easily store them in other Servers, So that we can recover them whenever a server fails.


## VM Setup

- We can setup the virtual machine manually and automatically. But you might face some issues if you are setting the VM Manually. Those are :

  1. First we need to download the iso file of the respective OS manually.

  2. Setting Up the virtual machine is time consuming because we need to follow so many steps to set it up.

  3. Since it is manual process there might be some human errors.

  4. It is tough to replicate the VM as we need to follow entire steps again which is time consuming.

  5. Since it involves lot steps a proper documentation is required.

  6. If you unfortunately delete the VM then we cannot recover it back and it takes a lot of time to create the same VM. So disaster recovery is difficult.


- To overcome all these issues, we can setup the VM automatically by using few commands. To set the VM automatically we actually use the software called `vagrant`.

- **Vagrant** is an open source software which is used to provsion the development environment quickly. It creates virtual environments by just executing few commands.

- Vargrant doesn't need any OS installation as it provides free VM images (called as Boxes) situated in vagrant cloud. All the changes we need to install while provisioning a VM is handled by a single file called Vagrant File. We generally use this vagrant file to create virtual machines.

- Vagrant provides simple commands to provision the Virtual Macines. Those are :

  **vagrant init** : It creates vagrant file in our current local directory which includes all the settings of the virtual machine.

  **Syntax** : `vagrant init box-name`

  **vagrant up** : It creates virtual machine in the virtual box.

  **vagrant status** : It gives the status of all VM's present in the Virtual Box

  **vagrant destroy** : It actually deletes the virtual machine in the virtual box

  **vagrant halt** : It shutdown the current running virtual machine

  **vagrant box list** : It gives all VMs present in the Virtual Box.

  **vagrant global-status** : It gives the status of all the VMs present in the Virtual Box.

  **vagrant ssh** : It is used to login into the virtual machine that is currently running.

- **Working of Vagrant** : Once we run the `vagrant init box-name` then vagrant fetches the vagrant file of that image from the vagrant cloud and places it in current directory. When you run the `vagrant up`, vagrant actually looks for the VM box or image in our current directory, if it doesn't find it then it actually downloads that VM image or box from vagrant cloud and then it creates the VM in the virtual box by effectively communicating with the hypervisor. After this we can perform anything on that virtual machine by using the above commands. This is actually procees being run in the background.


