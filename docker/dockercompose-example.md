### Redis

```yml
services:
  my-cache-server:
    image: redis
    ports:
      - 6379:6379
```

### MySQL

```yml
services:  
  my-db:  
    image: mysql  
    environment:  
      MYSQL_ROOT_PASSWORD: pwd1234  
    volumes:  
      - ./mysql_data:/var/lib/mysql  
    ports:  
      - 3306:3306
```
- `volume`을 활용

### Spring boot
- Docker Hun 같은 레지스트리에 올라온 공식 이미지를 사용하는 것이 아닌, `Application`을 컨테이너화 하는 경우에는 보통 `Dockerfile`을 작성해서 이미지를 빌드한다.
- 이때 `compose.yml`에서 `build`를 활용하여 `Dockerfile`을 활용

```dockerfile
FROM openjdk:17-jdk

COPY build/libs/*SNAPSHOT.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "/app.jar"]
```

```yml
services:  
  my-server:  
    build: .  
    ports:  
      - 8080:8080
```

```shell
docker compose up -d --build
```

### Nest.js
```dockerfile
FROM node  
  
WORKDIR /app  
  
COPY . .  
  
RUN npm install  
  
RUN npm run build  
  
EXPOSE 3000  
  
ENTRYPOINT ["node", "dist/main.js"]
```

```dockerignore
node_modules
```

```yml
services:  
  my-server:  
    build: .  
    ports:  
      - 3000:3000
```

```shell
docker compose up -d --build
```

### Next.js

```dockerfile
FROM node  
  
WORKDIR /app  
  
COPY . .  
  
RUN npm install  
  
RUN npm run build  
  
EXPOSE 3000  
  
ENTRYPOINT ["node", "dist/main.js"]
```

```dockerignore
node_modules
```

```yml
services:  
  my-server:  
    build: .  
    ports:  
      - 80:3000
```

```shell
docker compose up -d --build
```

### nginx

```dockerfile
FROM nginx  
COPY ./ /usr/share/nginx/html
```

```yml
services:  
  my-web-server:  
    build: .  
    ports:  
      - 80:80
```

```shell
docker compose up -d --build
```