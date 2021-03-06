#### --> Search for Docker Image
docker search <imagename>

#### --> By default, Docker will run a command in the foreground. To run in the background
docker run -d <imagename>

#### -->By default, Docker will run the latest version available. If a particular version was required
docker run  -d <image:version>

#### -->Lists all running containers, the image used to start the container and uptime
docker ps

#### -->Provides detailed information on constructs controlled by Docker. Info shall be in a JSON array
docker inspect <imagename or container-id>

#### -->Fetch the logs of a container
docker logs <container-id or image-name>

#### -->If a service needs to be accessible by a process not running in a container, then the port needs to be exposed via the Host.
Once exposed, it is possible to access the process as if it were running on the host OS itself.
docker run -d -p <host-port:containerport> <image-name:version>

#### -->To know which port has been assigned
docker port <name> <port>
#### --> For listing the containers displays the port mapping information
docker ps

#### --> Containers are designed to be stateless. Binding directories (also known as volumes) is done using 
-v <host-directory:container-directory>

#### -->Create your Dockerfile for building your image
In this example, our base image is the Alpine version of Nginx. This provides the configured web server on the Linux Alpine distribution.
FROM nginx:alpine
COPY . /usr/share/nginx/html
The first line defines our base image. The second line copies the content of the current directory into a particular location inside the container.

#### --> Docker Swarm
> To initialize swarm
docker swarm init 
> To join as a worker / manager
docker swarm join --token <worker/manager token> <host ip>:<port>  
> List nodes
docker node ls                     
> Create a new overlay network
docker network create -d overlay <network name>          

#### -->The build command executes each instruction within the Dockerfile. The result is a built Docker Image that can be launched and run your configured app.
docker build -t <name> <build-directory>
-t helps giving name for the image as your choice.

Run the newly creatd docker = docker run -d -p <host-ort:container-port> <name:ver>

#### --> We can access the standard out and standard error outputs using
docker logs redis-server.
The Syslog log driver will write all the container logs to the central syslog on the host. 
docker run -d --name redis-syslog --log-driver=syslog redis

#### --> With linking we don’t need to expose the source container
--link <name or id>:alias
Where name is the name of the container we’re linking to and alias is an alias for the link name.

#### --> To prevent sensitive files or directories from being included by mistake in images, you can add a file named .dockerignore
echo <file-to-ignore> >> .dockerignore
> We can use it to exclude files which we don't want to be sent to the Docker Build Context during the build.
echo <file> >> .dockerignore
When we rebuild the image, it will be much faster as it doesn't have to copy the 100M file.
docker build -t <name> .
