# Example 2 - Run Mulitple Containers

## Task/Requirements
1. Create 3 docker containers 
    - [ ] nginx
    - [ ] mysql
    - [ ] apache

2. Run all of them in the `detached` mode and provide a name to each container

3. Configure the port binding as follows: 
    - [ ] nginx -> 80:80
    - [ ] httpd -> 8080:80 
    - [ ] mysql -> 3306:3306

4. When running the `mysql` container, use the **--env** option (or **-e**) to pass in `MYSQL_RANDOM_ROOT_PASS=yes`

5. Use `docker container logs` to find the password issued to the `mysql` container. 

6. Clean up the containers with **docker container stop** and **docker container rm** commands (both can accept multple ids or names)

## Answer

1. First create the containers using the `docker container run` command
```s
docker container run --publish 80:80 -d --name proxy nginx && \
docker container run --publish 8080:80 -d --name web-server httpd && \
docker container run --publish 3306:3306 -d -e MYSQL_RANDOM_ROOT_PASSWORD=yes --name mysql_db mysql
```

2. List the newly created containers running the `docker ps` command
```s
docker ps
```

Results in: 
```s
grodriguez@Scotts-MacBook-Pro-2 RM-K8Demo % docker ps 
CONTAINER ID   IMAGE                  COMMAND                  CREATED          STATUS          PORTS                               NAMES
dd8d3a300427   mysql                  "docker-entrypoint.s…"   5 seconds ago    Up 5 seconds    0.0.0.0:3306->3306/tcp, 33060/tcp   mysql_db
1e70d6de225f   8c2c38aa676e           "/kube-vpnkit-forwar…"   8 minutes ago    Up 8 minutes                                        k8s_vpnkit-controller_vpnkit-controller_kube-system_c7e66e4a-dbe9-4498-85d5-2fc05c381731_1234
5759f968e487   httpd                  "httpd-foreground"       13 minutes ago   Up 13 minutes   0.0.0.0:8080->80/tcp                web-server
00b2de9bbf7e   nginx                  "/docker-entrypoint.…"   13 minutes ago   Up 13 minutes   0.0.0.0:80->80/tcp                  proxy
da84deb27689   mongo                  "docker-entrypoint.s…"   4 hours ago      Up 4 hours      27017/tcp                           mongo
```

3. Copy the contianer id for the mysql container and run `docker container logs <container id>` to retrieve the randomly generated password

```s
docker logs dd8d3a300427
```

In the output you'll see a log that looks like this ... 

```s
...
2022-05-08 22:12:51+00:00 [Note] [Entrypoint]: GENERATED ROOT PASSWORD: Q3AwzQE5+8NshUyv78s7vNOWD0HopzWS

...
```

4. Clean up all the containers

```s
docker container stop mysql_db web-server proxy && docker container rm mysql_db web-server proxy
``` 