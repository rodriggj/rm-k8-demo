# Docker Core Concepts

## Objective
- [ ] What is the difference between an `image` and a `container`? 
- [ ] Where can I find existing docker images? 
- [ ] What is a container actually? 

----

## What is the difference between an `Image` and a `Container`?

**Image** 
> An image is the application we are trying to run to include all the source code and binaries. 

**Container**
> A container is an instance of the _Image_ running as a process. 


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

---