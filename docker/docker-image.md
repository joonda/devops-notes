### MySQL
[MySQL-dockerhub](https://hub.docker.com/_/mysql)
- run MySQL in docker environment
```shell
docker run -e MYSQL_ROOT_PASSWORD=password123 -d -p 3306:3306 mysql
```

- environmental variables check
```shell
docker exec -it 84e bash
echo $MYSQL_ROOT_PASSWORD 
```

### PostgreSQL
[postgreSQL-dockerhub](https://hub.docker.com/_/postgres)
```shell
docker run -e POSTGRES_PASSWORD=password123 -p 5432:5432 -d postgres
```

### MongoDB
[Mongo-dockerhub](https://hub.docker.com/_/mongo)
```shell
docker run -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=password123 -p 27017:27017 -d mongo
```