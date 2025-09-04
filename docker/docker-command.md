### docker image
- image download
```shell
docker pull nginx
```

- show image list
```shell
docker image ls 
```

- remove docker image
- 84e -> first 3 word in docker image id
```shell 
docker image rm 84e
```

- remove docker image (force)
- delete the image of the suspended container, but not the image of the running container
```shell
docker image rm -f 84e 
```

- delete the entire unused image
```shell
docker image rm $(docker images -q)
```

### docker container
- create container
```shell
docker create nginx  
```

- run container
```shell
docker start 84e 
```

- create and run container (at the same time)
```shell
docker run nginx 
```

- create and run container (background)
```shell
docekr run -d nginx
```

- search docker container list
```shell
docker ps 
```

- search all docker container list
```shell
docker ps -a
```

- stop container
```shell
docker stop 84e
```

- forced shutdown container
```shell
docker kill 84e
```

- remove container
```shell
docker rm 
```

- remove stopped container
```shell
docker rm $(docker ps -qa) 
```

### container log
- check logs (while background)
```shell
docker logs 84e
```

- real time check logs
```shell
docker logs -f 84e 
```

### connecting container
- connecting to the inside of the container
```shell
docker exec -it 84e bash
```

### docker volume
```shell
docker run -e MYSQL_ROOT_PASSWORD=password123 -d -p 3306:3306 -v local-directory:container-directory
```
