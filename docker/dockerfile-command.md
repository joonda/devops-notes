### Build & Run
- `my-server` is docker image name to be created
- `.` is relative path where `Dockerfile` currently exists.
```shell
docker build -t my-server .
docker run -d my-server
```

### FROM
- Create Base image
- if without Tag name, it use LTS version
```Dockerfile
FROM openjdk:17-jdk
```
- `FROM [image-name]` 
- `FROM [image-name]:[tag-name]`

### COPY
- Copy a file
```Dockerfile
FROM ubuntu

COPY app.txt /app.txt
```
- Copy a Directory
```dockerfile
FROM ubuntu

COPY my-app /my-app/
```
- Copy a File Extension
```dockerfile
FROM ubuntu

COPY *.txt /text-files/
```

### IGNORE
- Use a `.dockerignore`
```dockerignore
readme.txt
```

### ENTRYPOINT
- `ENTRYPOINT`는 컨테이너가 생성되고 최초로 실행할 때 수행되는 명령어
```dockerfile
FROM ubuntu

ENTRYPOINT ["/bin/bash", "-c", "echo hello"] 
```

### RUN
- `RUN`은 이미지 생성 과정에서 명령어를 실행시켜야할 때 사용
```dockerfile
FROM ubuntu
RUN apt update && apt install -y git
ENTRYPOINT ["/bin/bash", "-c", "sleep 500"]
```

#### RUN vs. ENTRYPOINT
- `RUN`은 이미지 생성 과정에서 필요한 명령어 실행시킬 때 사용
- `ENTRYPOINT`는 생성된 이미지를 기반으로 컨테이너를 생성한 직후 명령어를 실행시킬때 사용

### WORKDIR
- `WORKDIR`로 작업 디렉터리 전환시, 그 이후에 등장하는 모든 명령문은 해당 디렉터리를 기준으로 실행
  - 컨테이너 내부 폴더 관리 용이
- `WORKDIR [작업 디렉터리로 사용할 절대경로]`
```dockerfile
WORKDIR /usr/src/app
```

### EXPOSE
- 컨테이너 내부에서 어떤 포트에 프로그램이 실행되는 지를 **문서화**하는 역할
- 즉, 작동하는 데에는 영향을 미치지 않는다 (참고 문서용)
```dockerfile
EXPOSE 3000
```