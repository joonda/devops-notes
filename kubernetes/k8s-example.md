### Pod (Nginx)

`yaml`
```yaml
apiVersion: v1
kind: Pod

metadata:
  name: nginx-pod

spec:
  containers:
    - name: nginx-container
      image: nginx
      ports:
        - containerPort: 80
```
- `apiVersion`: Pod 생성 버전, v1이라고 기재 (공식 문서)
- `kind`: Pod를 생성한다고 명시
- `metadata`: Pod의 이름 지정
- `spec`
  - `name`: 생성할 컨테이너의 이름
  - `image`: 컨테이너를 생성할 때 사용할 `Docker` 이미지
  - `ports` 해당 컨테이너가 어떤 포트를 사용하는 지 명시적으로 표현 (문서화의 개념)

### Spring Boot

- `Dockerfile`
```Dockerfile
FROM openjdk:17-jdk

COPY build/libs/*SNAPSHOT.jar /app.jar

ENTRYPOINT ["java", "-jar", "/app.jar"]
```
- build Docker image
```shell
docker build -t spring-server .
```
- `spring-pod.yaml`
- we used `IfNotPresent` policy to pull image
```yaml
apiVersion: v1
kind: Pod

metadata:
  name: spring-pod

spec:
  containers:
    - name: spring-container
      image: spring-server
      ports:
        - containerPort: 8080
      imagePullPolicy: IfNotPresent
```
- create pod, exec into pod, and curl
```shell
kubectl apply -f spring-pod.yaml
kubectl exec -it spring-pod -- bash
curl localhost:8080
```
- port-forward
```shell
kubectl port-forward spring-pod 8080:8080
```

### Nest.js

- `Dockerfile`
```Dockerfile
FROM node

WORKDIR /app

COPY . .

RUN npm install

RUN npm run build

EXPOSE 3000

ENTRYPOINT ["node", "dist/main.js"]
```
- build Docker image
```shell
docker build -t nest-server .
```

- `nest-pod.yaml`
```yaml
apiVersion: v1
kind: Pod

metadata:
  name: nest-pod

spec:
  containers:
    - name: nest-container
      image: nest-server
      imagePullPolicy: IfNotPresent
      ports:
        - containerPort: 3000
```

### nginx

- `Dockerfile`
```Dockerfile
FROM nginx
COPY ./ /usr/share/nginx/html
```

- build Docker image
```shell
docker build -t my-web-server .
```

- `web-server-pod-yaml`
```yaml
apiVersion: v1
kind: Pod

metadata:
  name: web-server-pod

spec:
  containers:
    - name: web-server-container
      image: my-web-server
      imagePullPolicy: IfNotPresent
      ports:
        - containerPort: 80
```

### Next.js

- `Dockerfile`
```Dockerfile
FROM node:20-alpine

WORKDIR /app

COPY . .

RUN npm install

RUN npm run build

EXPOSE 3000

ENTRYPOINT ["npm", "run", "start"]
```

- `dockerignore`
```dockerignore
node_modules
```

- build Docker image
```shell
docker build -t nest-server .
```

- `next-pod.yaml`
```yaml
apiVersion: v1
kind: Pod

metadata:
  name: next-pod

spec:
  containers:
    - name: next-container
      image: next-server
      imagePullPolicy: IfNotPresent
      ports:
        - containerPort: 3000
```