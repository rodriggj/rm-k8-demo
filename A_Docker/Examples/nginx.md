# Example 1 - Run an `nginx` container

## What is `nginx`? 

## Where can I find the `nginx` image? 

## How do I run the `nginx` container? 

1. Open a terminal window and run the following command

```s
docker container run --publish 8888:80 nginx
```

2. Navigate to a browser session and enter 
```s
localhost:8888/
```
And you should see the `nginx` webserver default home page.

3. So what just happened: 
```s
1. You told the `docker engine` to go download the latest image of nginx from DockerHub
2. You started a new container of the `nginx` image
3. You opened a port on your host (localhost), `8888` and mapped (bind) to port `80` on your container.
4. And because no flags were specified you iniated this container as a `foreground` process
```
As you hit refresh you see logs of the foreground process being rendered in your terminal. 

> To exit the existing process on a `MAC` you will hit `Ctrl-C`. On Windows `Ctrl-C` will exit the foreground process but process will continue to run in the background. So if on a Windows machine hit `Ctrl-C`, then in the terminal window you'll need to run:
```s
docker container ls -a                 # this will list all running containers, look for the Container Id of the nginx container, copy this id
docker container stop <container id>   # this will stop the container
```

4. To run the process in the background, execute the following command: 

```s 
docker container run --publish 8888:80 --detach nginx
```

> While this process is running in `detach` mode you won't see any foreground output in the console. If you want to see the logs for the container input the following command: 
```s
docker logs <container Id>
```

