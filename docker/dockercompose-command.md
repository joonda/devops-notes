### docker compose

- `compose.yml`에서 정의한 것을 기반으로 컨테이너를 `foreground` 에서 실행
```shell
docker compose up 
```
- `compose.yml`에서 정의한 것을 기반으로 컨테이너를 `background` 에서 실행
```shell
docker compose up -d
```

- `compose.yml`에서 정의된 컨테이너 중, 실행중인 컨테이너 조회
```shell
docker compose ps
```

- `compose.yml`에서 정의된 컨테이너 중, 종합적으로 로그를 출력
```shell
docker compose logs
```

- 이미지를 다시 build해서 컨테이너를 실행시켜야할 때 사용
```shell
docker compose up --build
```

- `compose.yml`에 정의된 이미지를 dockerhub에 있는 최신 이미지로 업데이트
```shell
docker compose pull
```

- `compose.yml`에서 정의된 컨테이너에서 실행중인 컨테이너 종료 및 삭제
```shell
docker compose down 
```