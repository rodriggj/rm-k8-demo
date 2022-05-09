# Docker Core Concepts

## Objective
- [ ] When people say "Use Docker ... " what exactly does that mean? 
- [ ] What is the difference between an `image` and a `container`? 
- [ ] Where can I find existing docker images? 
- [ ] What is a container actually? 
- [ ] Can I run Docker on Windows? 

----

## When people say, "Use Docker ..." what does that mean? 

<p align="center">
    <img width="400" alt="image" src="https://user-images.githubusercontent.com/8760590/167431195-c9869a90-bbcc-47aa-b92f-7e1776c6a75d.png">
</p>

-----

## What is the difference between an `Image` and a `Container`?

**Image** 
> An image is the application we are trying to run to include all the source code and binaries. 

**Container**
> A container is an instance of the _Image_ running as a process. 

<p align="center">
    <img width="400" alt="image" src="https://user-images.githubusercontent.com/8760590/167431427-60096e6e-808b-4a27-8060-4acd012ce67c.png">
</p>

**You can have `many` containers running the same image.**

**Example:**
Image: nginx:9.2
Container: Web-server (Auth Service, Payments Service, Location Service), Proxy, Load-balancer

-----

## Where can I find existing docker images? 

**Dockerhub**
> Docker's default image `registry` is called _Dockerhub_ [hub.docker.com](https://www.hub.docker.com)

**Private Repositories**
> Enterprises can purchase, create, or subscribe to private repositories maintained by Dockerhub or other sources. 

-----

## Run `hello-world` docker container
> Every technology has a _happy path_ implementation that demonstrates core concepts. Docker is no different. Execute the following `hello-world` excercise. 

1. After installing the Docker Desktop, which will include the Docker Client, run the following command: 
```s
docker run hello-world
```

2. View the output of the console.

3. The process in a picture

<p align = "center">
    <img width="400" alt="image" src="https://user-images.githubusercontent.com/8760590/167439293-ac54d8d9-c28f-41b1-89a6-28ace31e9a57.png">
</p>


## What is a container actually? 
> `docker` is not a "VM" comparable. Docker is simply a process running on the underlying Linux host. 

Example: 
1. Run a docker image 
```s
docker run --name mongo -d mongo
```

2. Now run the following command to validate that there is a process running for the container you just created
```s
docker top mongo
```

3. Now run all the processes that are currently running on your host 
```s 
ps aux | grep mongo
```

4. Now we can see that this is just a process running on our host.

5. Picture to describe this process. 

_Without Containers_
<p align =  "center">
    <img width="400" alt="image" src="https://user-images.githubusercontent.com/8760590/167444201-f1af05a0-d3f2-4eeb-9d10-60191d7609b6.png">
</p>

_With a Container_
<p align = "center">
    <img width="400" alt="image" src="https://user-images.githubusercontent.com/8760590/167451575-df2ccf0a-189e-4503-9374-cd5ff77a8602.png">
</p>
---

## Can I run Docker on Windows? 
> Not all Operating Systems and Kernals are buitl the same. Even amongst Linux distributions the operating system functions are different. So this begs the question, can we run containers on Windows, when all the documentation keeps calling out the need for Linux?

_Take one example of Kernal / Operating System differences ---> _Namespacing_ and _cGroup_ capability...
<p>
    <img width="400" alt="image" src="https://user-images.githubusercontent.com/8760590/167446261-459958c3-71eb-44f5-a2c0-78f6f917435d.png">
</p>


