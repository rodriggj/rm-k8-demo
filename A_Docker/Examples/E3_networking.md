# Docker Networking

1. First start a container 

```s
docker container run -p 80:80 --name webhost -d nginx
```

2. Run the docker command to view the ports mapped to this container

```s
docker container port webhost
```

3. We can also see the IP address of the container by running the inspect command. But we don't want to see all the inspect output so we can use the `format` argument with the `{{ }}` syntax to refer to the node in the json payload that we want to see. We can accomplish the same with the `grep` command, but the format command is cleaner. 

```s
docker container inspect --format '{{ .NetworkSettings.IPAddress }}' webhost
```
> Note the IP address of the host and the container are not the same. This is because Docker establishes a default network and assigns the CIDR block via a NAT traversal to the host. If you run `ifconfig en0` on your Mac you can compare the two different IPs. 

