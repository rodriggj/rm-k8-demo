# Docker Commands

### 1. Docker Version
> Verifies that your CLI can talk to the Docker Dameon.
```s
docker version
```

### 2. Docker Info
> Provides most of the configuration details needed when attempting to ensure compability with target env.
```s
docker info
```

### 3. Old vs. New Means of CLI syntax
```s
# Old
docker <command> (options)

# New 
docker <command> <sub-command> (options)
```

### 4. All commands in Docker
> Use this command if you need to get a list of commands available to you or if you are in search of an example. This isn't the full list of commands, as now Docker has created _management_ commands. 
```s
docker 
```

### 5. Docker Run 
> The docker run command actually runs 2 distinct commands, 1. docker build and 2. docker apply in a consolidate `docker run` command`. 
```s
docker container run nginx
docker container run --publish 8888:80 nginx
docker container run --publish 8888:80 --detach nginx
```

### 6. List running containers
> The docker container management command will provide various ways to see container images on your host. Use this command when you need to identify a specific container and need the Id. 
```s
docker container ls   # this will list all running containers on your host. If the container IS NOT running you will not see the container listed
docker container ls -a    # this -a flag will list all container images on the host whether they are running or not
docker ps # the ps is an alias for the docker container ls -a command, it is a shortcut to display the same info as docker container ls -a
```

### 7. Stop running containers
> This command will stop, but not kill a running container. The image will still be available on your host unless you kill (aka delete) the image.
```s
docker container stop <container id>
docker container stop <container name>
```

### 8. See logs of the container 
> If you run a container in detached `--detached` mode you will not see the activity logs render to the terminal. You can still display this information via the docker logs command.

```s
docker container logs <container Id>
docker container logs <container name>
docker container top <conatiner name>   # this will provide the PID (process Id) of the processes running in the container 
```

### 9. Remove Container images
> Removes one or more containers

```s
docker container rm <container id>
```

### 9. See contents of a container
> There will be times when you need to see inside a container for the processes running, file structure, etc. To do so you can use the following commands

```s 
docker container top       # process list inside a contianer
docker container inspect   # details of one container config
docker container stats     # performance stats for all containers
```

### 10. Aside from seeing the contents of a container you may need to `SSH` into a container
> You will also need to "terminal" into a running container you may need to enter the container for actions. 

```s
docker container run -it --name proxy nginx bash  # Here you run the container in `interactive` mode with TTY session which will show as root user of the container
```

### 11. What if I want to rerun an existing container

```s
docker container start -ai <container name> # Here you are "restarting" an existing contianer in `attached` mode with `interactive` shell
```

### 12. What if I want to run additional commands beyond the boot command? 

```s
docker container exec -it  --name mysql bash  # Here you can run additional processes beyond the process at bootup
```