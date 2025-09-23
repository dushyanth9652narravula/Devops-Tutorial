# Introduction to Containerization

- Before virtualization, if you want to run different applications with different OS, we need seperate physical servers which wasted a lot of hardware resources and there are disadvantages by doing it. But virtualization fixed that by letting you run multiple virtual machines with multiple OS on same physical hardware.

- But even though we have advantages of virtualization, there are some problems in it. When we run multiple services inside same VM (or even inside the host machine without isolation), we hit many problems. Some of them are :

  **Dependency Conflicts** : Different services may require different versions of same library or runtime (e.g Pyhton 3.12 for one service, Python 3.9 for another). Installing them on same VM may cause conflicts.

  **Resource Consumption** : Services inside the same VM share CPU, RAM, disk I/O, and network. If one service starts using too many resources (e.g., heavy database queries), other slow down.

  **Security Risks** : If one service is compromised, the attacker may access other services inside the same VM since they share the OS kernal and environment.

  **Scaling Difficulty** : You can't easily scale just one service without scaling the whole VM. This means you waste resources when you want to increase the capacity for only one part of the workload.

  **Operational Complexity** : Updating one service without affecting others can be tricky. If you update a shared library for Service A, it might break Service B.

- But we might think that why can't we just run each service in its own VM. We can put each service in a seperate VM, but it has its own drawbacks :

  **Overhead** : Every VM runs a full OS, meaning high CPU and memory usage just for idle OS processes.

  **Startup Time** : Booting a VM takes seconds to minutes.

  **Maintainance** : If you run services idle in single VM, then there might be more OS updates which requires more storage and configuration works.

- So to overcome the problems with running multiple services in same machine, a new concept arised called containerization. Containerization is a software deployment method which actually packages the application and its dependencies into a standard unit called container for consistent and efficient execution across different computing environments.

- Containerization packages only the application and its dependencies, not the full OS. It actually shares the host OS kernal while keeping applications isolated in seperate runtime environments and it bootup in milliseconds because it is lightweight.

- In containerization, only process is running which is process of the service itself. Generally in linux, first process is `init` and all other process are child process of init. But if you created a container for mongodb then first process in that container is mongodb itself and all other process are child process of mongodb.

- With containerization, we can get the following benifits :

  **Isolation** : Each container has its own filesystem, libraries, and environment variables. So there is no dependency conflicts exists here.

  **Lightweight** : In containerization, we doesn't need the full guest OS for each service, reducing resource overhead.

  **Scalable** : We can scale just the container running one service without touching others.

  **Portable** : It works on every machine as problem goes away because it has all the dependencies.

- So we can say, running multiple VMs on same machine or VM, creates conflicts, scaling issues, and security risks because they share the same OS environment. But containerization emerged to solve this by isloating services without the heavy overhead of full VMs, making deployments faster, more secure and more resource efficient.

- So containerization is simply the virtualization of OS but this OS contains the files that are required for running the service.

## Intro to Docker

- Docker is an open platform for developing, shipping and running applications. Docker enables you to seperate the applications from our infrastructure, so we can deliver software quickly.

- Docker provides the ability to package and run an application in a loosely isolated environment called a container. This isolation and security lets you to run many containers simulataneously in a given host.

- Containers are lightweight and contain everything needed to run the application, so you don't need to rely on what's installed on the host. You can share containers while you work, and be sure that everyone you share with gets the same container that works in the same way.

- **Basic Docker Commands**: These commands are just used to run, stop, remove containers created by the docker.

  1. **Docker Run** : `docker run <image_name>` actually feteches the image from the dockerhub if it is not available locally and then starts running that container. This command has different options. Those are `--name` which is used to name the container, `-d` which is used to run the container in detached mode, `-p` which is used for port mapping and `-P` which assigs the host port automatically instead of manually like we have assigned using `-p`.

     **Ex** : `docker run --name web01 -p 9080:80 nginx` -> It actually creates a container with name as web01 on nginx image and gives access to host on port 9080.

  2. **Docker ps** : `docker ps` is used to display the running containers in the machine. If you want to display all the containers present in the machine then we need to use `docker ps -a`.

  3. **Docker Stop** : `docker stop <Container_name>` is used to stop the running container.

     **Ex** : `docker stop web101`

  4. **Docker Remove** : `docker rm <container_name>` is used to remove the container. We need to stop the container first before removing the container.

     **Ex** : `docker rm web01`

  5. **Docker Images** : `docker images` is used to display the images present in the system.

  6. **Docker Remove Images** : `docker rmi <image_id>` is used to remove the images present in the system. We can get the images id from the previous command.

  7. **Docker Build** : `docker build -t <image_name> <Dockerfile_path>` is used to build the custom image created by us. `-t` is used to name the image.

  

