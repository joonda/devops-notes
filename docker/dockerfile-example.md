### Spring Boot

```dockerfile
FROM openjdk:17-jdk

COPY build/libs/*SNAPSHOT.jar app.jar

ENTRYPOINT ["java", "-jar", "/app.jar"]
```

```shell
./gradlew clean build

docker build -t hello-server .

docker run -d -p 8080:8080 hello-server
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

```shell
docker build -t my-server .
docker run -d -p 3000:3000 my-server
```

### Next.js

```dockerfile
FROM node:20-alpine

WORKDIR /app

COPY . .

RUN npm install

RUN npm run build

EXPOSE 3000

ENTRYPOINT ["npm", "run", "start"]
```

```shell
docker build -t my-web-server .
docker run -d -p 80:3000 my-web-server
```

### HTML, CSS, Nginx
- Nginx를 사용하기 위해서는 HTML 파일명을 `index.html`로 지정해야한다.

```dockerfile
FROM nginx

COPY ./ /usr/share/nginx/html
```

```shell
docker build -t my-web-server .
docker run -d -p 80:80 my-web-server
```

#### docker ignore
```dockerignore
node_modules
```