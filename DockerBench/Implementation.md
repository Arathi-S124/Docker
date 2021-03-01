 Docker bench requires Docker 1.13.0 or later in order to run.
 
1. Docker bench has been packaged as a small container for our convenience. This container is being run with a lot of privilege -- sharing the host's filesystem, PID, and network namespaces, due to portions of the benchmark applying to the running host. So we shall go by the easiest way to run our hosts against the Docker Bench by running our pre-built container.

2. According to the OS, you can choose the command to run the Docker Bench container from- https://github.com/docker/docker-bench-security .

3. Run the command for assessing the host. 

#### Note:- Run the docker commands with sudo if a non-root user has not been created by you. 

![image](https://user-images.githubusercontent.com/62760235/109507216-80eb1200-7ac4-11eb-9897-771674b0b80e.png)

![image](https://user-images.githubusercontent.com/62760235/109507234-847e9900-7ac4-11eb-8f19-8ad840d88fbd.png)






