### About the tool

The Docker Bench for Security is a script that checks for common best-practices around deploying Docker containers in production.  Docker Bench (Maintained by Aqua Security Software Ltd.)  is written in Golang. The tests are automated and inspired by the CIS Docker Benchmark v1.2.0.

### Why Use This?

* Docker Bench is used for configuration audits. *

* This tool can be used to perform a security analysis on Docker and can find common configuration flaws that may impose risks to other containers or the host itself. *

* It has a command-line interface for usage.*

### Where to access it ?

You can download and run this tool from [here](https://github.com/docker/docker-bench-security).

### The features of new release :-

* Align with CIS Docker Benchmark v1.2.0. *
* Update and slim the default Alpine Dockerfile. *
* Added no-color option. *
* All tests are now functions. *
* Add support for running specific tests. *
* Add support to exclude specific containers or images. *

### Understanding the tool on Command Line :-

The script results in Info, Warning, and Pass notes for each of the configuration recommendations. These are grouped into 7 sections:

### 1. Host Configuration

![image](https://user-images.githubusercontent.com/62760235/109505451-9e1ee100-7ac2-11eb-993c-1a319fe53503.png)

![image](https://user-images.githubusercontent.com/62760235/109505490-a70fb280-7ac2-11eb-806b-d4c1df2e9f4b.png)

### 2. Docker Daemon Configuration

![image](https://user-images.githubusercontent.com/62760235/109506335-86942800-7ac3-11eb-979d-ffba803d7bde.png)

### 3. Docker Daemon Configuration Files

![image](https://user-images.githubusercontent.com/62760235/109506325-8431ce00-7ac3-11eb-8adb-d3581e3a7c76.png)
![image](https://user-images.githubusercontent.com/62760235/109506159-577db680-7ac3-11eb-9023-bf21fd8a8579.png)
![image](https://user-images.githubusercontent.com/62760235/109506250-711efe00-7ac3-11eb-9fe3-a8f8d330218e.png)

### 4. Container Images and Build Files

![image](https://user-images.githubusercontent.com/62760235/109506137-5187d580-7ac3-11eb-9934-f2c34ed32178.png)

### 5. Container Runtime

![image](https://user-images.githubusercontent.com/62760235/109506063-3e750580-7ac3-11eb-9f09-77a7bfcf1035.png)

### 6. Docker Security Operation

![image](https://user-images.githubusercontent.com/62760235/109505931-1a192900-7ac3-11eb-89b7-cc28bd097aa6.png)

### 7. Docker Swarm Configuration

![image](https://user-images.githubusercontent.com/62760235/109505913-15547500-7ac3-11eb-9820-fe6887cb17c3.png)


### Some flags that are available for the tool:-

* -b -> Do not print colors *
* -h -> Print this help message *
* -l  FILE -> Log output in file *
* -c CHECK -> Comma Delimited list of specific check(s) *
* -e CHECK -> Comma Delimited list of specific check(s) to exclude *
* -I  CHECK -> Comma Delimited list of patterns within a container/image name to check *
* -x CHECK  -> Comma Delimited list of patterns within a container/image to exclude *
