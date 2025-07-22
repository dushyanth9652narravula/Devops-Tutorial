# Server Configuration Using Vagrant

## Introduction

- As we know vagrant is used to provision the virtual machines automatically by using simple commands such as `vagrant init <boxname>`, `vagrant up`, `vagrant destroy` etc. But all these virtual machines created by vagrant are configured by a single file called `Vagrantfile`.

- Inorder to configure the VM as we required, we need to understand the code inside the Vagrantfile. We can configure the resources required for VM to run such as RAM, ROM, CPUs , Networking etc.

- Vagrantfile is written in Ruby Language. We doesn't need to learn Ruby Programming Language to understand the vagrant file. Vagrantfile starts with a simple syntax which is `Vagrant.configure('2') do |config|`. `Vagrant.configure('2')` represents that it is using the vagrant version 2 which is a stable version of vagrant. The `config` in between the pipe symbol is just an class object. Here we can name anything we want but we need to use the same object in all the code.

## Configuring the IP, RAM, CPUs of Virtual Machine

- After `Vagrant.Configure` the first thing we actually need to configure is what operating system we are using. If we are using linux what box we are using from vagrant cloud. To set up the Os or box we use `config.vm.box` syntax. For example if i want to use `ubuntu/focal64` then my syntax is `config.vm.box = ubuntu/focal64`.

- Generally we have two types of networking. One is Private IP address through which we can access the Virtual Machine by using host machine only. This Private IP address is used to test whether webserver in the virtual machine is running correctly or not. To set up the Private IP Address for the Virutal Machine we use `config.vm.network "private_network", ip : <ip_address>`. But while setting up th IP Address don't change 1st and 2nd octant, change only 3rd and 4th octant. In `192.168.33.10`, `33` and `10` are 3rd and 4th quadrants. 

- Second Networking is `public network` we creates a bridged network, so that we can access the VM from our devices such as Phone etc but both VM and your phone connected on same LAN. Here Ip address is dynamic which is assigned by the Router (Here we get IP address similar to we get ip address when we deploy streamlit app locally etc). So to enable this public network we use `config.vm.network "public_network"`.

- To configure CPU, RAM then we actually need to configure the virtual machine provider. If we are using Windows OS, we actually use VirutalBox as VM provider. If we are using MAC, we use VMWare as VM provider. To configure VM Provider, we use `config.vm.provider "<VM Provider>" do |<Any object name>|`. For example `config.vm.provider "virtualbox" do |vb|`. Under this we can use `vb.memory` to configure the RAM and `vb.cpus` to configure cpus etc.

## Configuring Vagrant Sync Directories

- Vagrant provides a nice feature called `Sync Directories` through which we can share the data between guest and host machine which means we can share data between personal computer and virtual machine. These `Sync Directories` are very useful when we want to edit some files present in virtual machine. Because virtual machines doesn't have fancy editors to edit certian files. So we edit those files through our computers if they are in shared directories.

- To add a sync directory vagrant provides a syntax which is `config.vm.synced_folder <host_path> <guest_path> options`. You will see this syntax below the `config.vm.network "public_network"` syntax. Here `host_path` is path of a directory in our local computer, `guest_path` is path of a directory in virtual machine to sync with the directory in local machine. `options` are used to control the behaviour of these sync directories.

- By default, the folder containing the vagrantfile and `/vagrant` acts as sync directories in host and guest machine. If go below after above syntax (`config.vm.synced_folder <host_path> <guest_path> options`) we have anothot syntax which is used to disable the default sync directroy when virtual machine gets created. The syntax is `config.vm.synced_folder "." "/vagrant" disabled : true`. If you uncomment this syntax then `/vagrant` and folder containing vagrantfile in our local machine doesn't share data each other.

- So the basic syntax to create sync directories between host (local computer) and guest machine (Virtual machine) is following :

  **Syntax** :`config.vm.synced_folder "<host_path>" "<guest_path>" options`

  **Ex** : `config.vm.synced_folder "../data" "/scripts"

  Here if `scripts` directory is not present in the virtual machine then vagrant automatically creates that scripts directory at the specified path.

## Provisioning in Vagrant

- Provisioning in Vagrant is nothing but process of setting up and configuring the virtual machine automatically after the VM is created. Provisioning can include tasks such as installing softwares, setting up the environment or configuring the services or applications in the Virtual Machine. 

- This provisioning is actually useful when we want to set an environment for testing team. We usually setup the VM other configurations normally but we also need to install respective softwares and setting up them and so on. So if you include all the code in vagrant provisoners then they automatically creates that environment and set it up for us.

- Uses of provisioning are :

  1. It automate the setup of environment
  2. It maintain the consistency across mutiple VMs
  3. By using provisioning we can recreate the test environment for depolyment.

- There are different types of provisioning in vagrant. The most common provisioning technique is `Shell Provisioner`. If you go to the end of the Vagrantfile, we have one setting called `config.vm.provision` which is responsible for provsioning.

  **Shell Provisioning** : Shell Provisioning is simply nothing but running whatever shell commands we have provided under this setting are automatically executed in virtual machine shell once the VM actually created not powerd on. There are actually two types of shell provisioning. Those are :

    **Inline** : In inline shell provisioning we actually provide all the commands or shell scripts in vagrant file itself for provisioning. 

    **Ex** : 

    ```ruby
    config.vm.provision "shell", inline: <<-SHELL

        echo "Running Shell Commands"

        sudo apt-get install -y httpd

    SHELL
    ```

    This commands only gets executed at the time of VM creation only. If you power off the VM and Power on then these commands won't gets executed. If you want to execute the provision commands even during power on then we have to use an additional option called `--provision` along with `vagrant up` which means we have to execute `vagrant up --provision` command. Otherwise we can execute `vagrant provision` command externally to provision the virtual machine even after the creation of VM.

    **External** : In this type of shell provisioning, we use external script file which contains shell commands instead of writing the shell commands internally in the vagrant file. The syntax for this type of provisioning is :

    **Syntax** : `config.vm.provision "shell", path: <Script_File_Path>`

- **Note** : Similarly we have other type of provisioning such as File Provisioning, Ansible Provisioning, Puppet Provisioning, Docker Provisionin. We need to provide respective names there instead of `"shell"` and provide respective commands instead of shell commands.

- The provsioning occurs automatically when you run `vagrant up`. But VM is not  provisioned everytime when you run `vagrant up`. The VM is only provisioned when VM is created for firstime. But you can manually trigger provisioning on an existing VM by running `vagrant provision`. If you want to re run provisioning while `vagrant up` we can run `vagrant up` command like this `vagrant up --provision`. If you don't want to provision you VM even when you are creating for the firsttime then  you create the Vm by running `vagrant up` like this `vagrant up --no-provision`.

## Hosting a Website on Virtual Machine Manually

- Before hosting a website om virtual machine, first lets us know what is webserver and what is the importance of the web server.

- **Web Server** : 

  1. A Web Server is a software that listens the HTTP/HTTPS requests from the client (like browser) and responds with appropriate content such as HTML pages, images or data etc.

  2. For example, when you enter `http://192.168.56.22` in your browser, your browser send the HTTP Request to the IP address. Then web server running on that IP listens for the request and responds with the requested resource if it is found else it throws an error if resource is not found.

  3. Without web server, the browsers Http request wouldn't hit the VM as there is no program to interpret that request, so the browser would show error like connection refused or unable to connect.

  4. Some of the common web servers are `Apache`, `Nginx`, and other light-weight servers such as `python3 -m http.server 80` etc.

- To host a website on VM, first we need to install webserver which is httpd on Centos and apache on linux. So to install webserver `httpd` we need to use this command `yum install httpd`

- Once we installed `httpd`, we need to start the service using `systemctl start httpd` command. Once the service is started then we actually need to enable the service using `systemctl enable httpd`. Now we need to deploy the website content on the Virtual Machine. Generally Linux distros store all websites content in `/var/www/html` directory. Here we need to place the `index.html` and other related content of the website (But webserver generally opens that file only when we access the ip address). Once we placed all the content of the website in `/var/www/html`, just restart the service by runing `systemctl restart httpd` or `systemctl reload httpd`.

## WordPress Setup in Ubuntu

- To setup the Wordpress just follow the guidelines provided in the wordpress setup website in google. The only difference I have observed is for hosting a website we used `/var/www/html` directory. But for hosting a complete service, we have used a `/srv/www/` directory. Because `/srv/www` is convinient for hosting multiple services where as in `/var/www/html` is not convinient for hosting multiple websites or services.

## Automating Website Setup and Wordpress Setup Using Vagrant Provisioning

- Till now, we have hosted a website and wordpress in the VM Manually. Now lets automate it by vagrant provisioning. We can simply automate the steps of website setup by just writing the commands that we have run for setting up website under vagrant provisioning part in vagrantfile of that VM.

- So the inline shell commands for website setup are :

  `yum install httpd wget unzip -y`

  `systemctl start httpd`

  `systemctl enable httpd`

  `mkdir -p /tmp/finance`

  `cd /tmp/finance`

  `wget https://www.tooplate.com/zip-templates/2135_mini_finance.zip`

  `unzip -o 2135_mini_finance.zip` -> -o for overriding the files.

  `cp -r 2135_mini_finanace/* /var/www/html`

  `cd /tmp`

  `rm -r finance`

  `systemctl reload httpd`

- Similar to automation of website setup, we can automate the Wordpress setup by just keeping all the commands in Vagrantfile under `config.vm.provision`.
