

### Openshift

#### Local Development 
Containers are developed by developers locally. Developers can use openshift Local or Intalled Openshift cluster.
Install Openshift Local instructions available at https://console.redhat.com/openshift/create/local ( as of 12/22/2025 )

### Docker Commands

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

#### Creating Image
use -d to run it in backgroud. docker run mysql can be stopped with CTRL+C. --name to use a name. Container image specifies the command to start the process inside the container ( we can specify a different one)
-t and -i are needed for interactive command. -e for passing parameters

> docker run mysql
> docker run -d mysql:5.5
> docker run -d --name msql mysql:5.5
> docker run --name msql -it mysql  /bin/bash


