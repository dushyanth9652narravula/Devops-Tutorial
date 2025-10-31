# Vprofile Project

- Vprofile Project is simply nothing but hosting a java based web application on virtual machines. By doing this project, we can just know how to connect mutiple services to build an application stack.

- For this project we actually using 5 services. Those are :

  1. **Nginx** : `Nginx` is actually a web server which is generally used to host the static web pages. Generally we use Apache httpd, Apache Tomcat to host web pages. But these services cannot able to process the huge trafic. To process requests from huge traffic, a new service introduced called `Nginx` which is primialry used as load balancer. `Nginx` can be used as web server but may not able to host big projects. It can able to store the static HTML/CSS content such as login pages or most requested page as cache nd when ever it got request for that page, it directly render that page in the browser without even interacting with actual web browser.


  2. **Tomcat** : `Tomcat` is an java based web server which can be able to host java based web applications.

  3. **MySql** : `MySql` is a database server which canbe used to store the user login data here.

  4. **Memcache** : `Memcache` is a service which is used to cache the most accessed data by an user. When an user actually asks for data first tomcat sends requests to mysql for that data and then mysql sends the require data for tomcat. In between both a caching service called `Memcache` is situated which stores most accessed data by that user as a cache. Whenever user again requests for that data then `Memcache` sends that data to tomcat instead of from `mysql`.

  5. **Rabbitmq** : RabbitMQ is a message broker — it helps different parts of a system communicate with each other asynchronously and reliably by passing messages between them. Think of RabbitMQ as a post office: Your application (like a sender) puts messages into a queue, Another application (like a receiver) picks up messages from the queue and RabbitMQ ensures the messages are delivered safely, in order, and only once.

- Here we have two ways to do this project. First we can set it up manually by installing all the services and then we configure those services in the VM and then we can set the entire stack automatically by using `vagrant provisioning`.

- **Manual Workflow** : Follow the pdf in the zip file and use the mutlivm vagrant file for creating the Vms. [Vprofile Project Manually](../_static/vprofile_Project_manually.zip)

- **Automatic Workflow** : Just extract the zip file attached here and open this folder in gitbash and just run `vagrant up` for creating and provisioning the application stack. [Vprofile Project Automatically](../_static/vprofile_Project_Automatically.zip)