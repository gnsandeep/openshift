

### Openshift

#### Local Development 
Containers are developed by developers locally. Developers can use openshift Local or Intalled Openshift cluster.
Install Openshift Local instructions available at https://console.redhat.com/openshift/create/local ( as of 12/22/2025 )

### Docker Commands

There are some docker commands that change container state , some commands that query the container state.

#### Creating Container
docker run command creates the container from an image. It will download the image if needed. It will start a process inside the container. Stop it with Ctrl+C. This command generates random name and id for the started container.

use -d to run it in backgroud.  --name to use a name. Container image specifies the command to start the process inside the container ( we can specify a different one)
-t and -i are needed for interactive command. -e for passing parameters

> docker run mysql
> docker run -d mysql:5.5
> docker run -d --name msql mysql:5.5
> docker run --name msql -it mysql  /bin/bash
> docker run --name msql -it mysql dd if=/dev/zero of=/dev/null

when a specific command is provided , docker does not run the default command specified in the image. Container may stop after executing the command. dd command in the example is also a commmand.

##### Storage
When containers are created , they get container storage . Container storage is  a layer above the image layer. Cotainer storage is destroyed with container ( docker rm container-name). We can mount host directory to a container using -v in docker run command

docker run -v /var/dbfiles:/var/lib/mysql mysql # other options

Note: /var/lib/mysql alredy exists inside the container. it is overlayed by /var/dbfiles.

#### Query
docker ps provides details of  running containers. docker ps -a gives the list of containers that are stopped also.

docker inspect command is used for listing metadata about running or stopped container. -f can be used for formatting the output

docker inspect -f '{{ .Networksettings.IPAddress }}' my-httpd-container.
docker inspect my-http-container | grep IPAddress

docker ps has -q that returns IDs.
docker ps -aq will return ids of all containers

docker logs container-name will get the logs

#### Update 

##### exec
docker exec command can be used to start another process inside the container.
docker exec my-container cat /etc/hostname
docker exec -it container-name  /bin/bash ( to get in to the container 


##### stop , restart 
docker stop container-name 
docker start container-name
docker kill container-name will force stop the container
docker restart container-name will restart the container
docker rm container-name will delete the container

docker rm $(docker ps -aq)
docker stop $(docker ps -q)

Note: container-name or container-id will work

#### Network
Docker Engine uses bridged Network mode, which through the use of iptables , NAT and virtual switch allows containers to talk to other containers and host machine.

We can map network ports using -p

docker run -d --name httpd -p 8080:80 dp276/httpd

request received by the host on port 8080 is sent to container port 80. you can specify ip address


#### Search Image
To Search for a Image. Search docker hub container registry. ?Check how to add local registry?
> docker search mysql

#### Pull Image
To pull a image . If no tag name is provided in the pull command then tag with name latest is pulled.
> docker pull mysql
> docker pull mysql:5.5

#### List Images
> docker images

REPOSITORY entry contains repo url/user name/image and tag

#### Delete Image
docker rmi image-name




