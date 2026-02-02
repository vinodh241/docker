# Docker:#  BY VINODH AVALA
---------------------------

* Hypervisor
--------------
Hypervisor oe Virtual Machine Monitor (VMM), is software that enables a single physical host machine to run 
manage and provision multiple isolated virtual machines (VMs).

* VM
-------------
Logically devides physical hardware into multiple servers 

* IMAGE:
----------------
IMAGE =  Base min OS + system packages + Application code and dependencies = ( ex:500MB)

    VM                      vs               container
----------------------------------------------------------------------------
1. cost                     |            less cost 
2. Moretime (boot time)     |            less time (boot time)
3. more size                |            small size
4. more resources           |            less resources 
5. block the resources      |            Dynamic resource allocation
6. Hypervisor               |            no need of any extra software
7. Not portable             |            portable
8. More secure              |            less secure (we can achive security)
--------------------------------------------------------------------------------

* Docker:
--------------
 * install Docker commands:
    -----------------------------
_-----------------------------------------------------------------------------------------------------------
    sudo dnf -y install dnf-plugins-core
    sudo dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo
    sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
 -----------------------------------------------------------------------------------------------------------   

Add your normal user to docker
 * by default we cant get the direct access for docker engine, for getting access to docker we have to add our user to docker group

* sudo usermod -aG docker ec2-user 

----------------------------------------------------------------------------------------------------------
Docker commands:
---------------

* docker ps -- Running containers 
* docker ps -a -- Running + stopped conatiners ( All)
* docker images -- images available on your system

Docker IMAGE:
-------------

docker image: 

docker pull <image-name>:<tag/version>  -- download the images form central repo 

* docker rmi <image_id/image_name> -- remove the image


Docker Container:
----------------

container is nothing but running instance of image

    * it is also a mini server 

* docker create <image-name>/nginx -- creates a container 

* docker start <container_id/containername> -- start the container

* docker stop <container_id/containername> -- stop the container

* docker rm <container_id/containername> -- remove the container

* docker run <image_name/image_id>:tag   -- it will pull the image form central repo + creates container + start container too 

* docker run -d <image_name/image_id>:tag -- detach mode run the container in background 

* docker ps -a -q -- to get the all container ID's

* docker rm -f `docker ps -a -q` -- it will remove all containers ( stopped+ running containers )

* docker run -d -p --name <name> <imagename>:tag  -- to specify the name for container 



docker port mapping:
--------------------

docker run -d -p    80 :   80  nginx
                    |       |
                hot-port  container-port

    * here host port anything itr our wish but container port should be 80 only , bcz nginx listing port 80 only 

* docker run -d -p 80:80 nginx:latest 


    * we can't use host port agian ( ex: port 80 allocated to nginx container-1 , but we cant use same port for container -2 )
    * when you use docker run command every time one container will create (container port 80 we can use , every time new container created (i;e 0-65568 ports). if you want create another container then use diff host port

    * docker run -d -p 81:80 naginx:v1.0 

* docker run -d -p --name <name> <imagename>:tag  -- to specify the name for container 

    * we cant use same name and same host for another container, if you want use diff name & host port for another container 

* docker exec -it <container_name/contianer_Id> bash -- to login to the inside container 

 * CTRL + P + Q -- exit from  running container with out stopping ( container ) 

 * docker inspect <containername/container_id>  -- to check the container IP address 


How can you create custom images to your applications?
-----------------------------------------------------------------------------------------

using Dockerfile we can create custom images 

# Dockerfile:
   ----------

   A set of instructions to create customized images

   FROM almalinux:tag  -- Dockerfile must should start from FROM instrutions

















