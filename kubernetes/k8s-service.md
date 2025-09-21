### Service

```yaml
apiVersion: v1
kind: Service

metadata:
  name: spring-service

spec:
  type: NodePort
  selector:
    app: backend-app
  ports:
    - protocol: TCP
      port: 8080
      targetPort: 8080
      nodePort: 30000
```

`type`
- `NodePort`: 클러스터 내부와 외부에서 모두 접근 가능하도록 `Node`에 고정 포트를 할당.
- `ClusterIP`: 클러스터 내부에서만 접근 가능, 외부에서는 접근 불가
- `LoadBalancer`: 클라우드 제공 로드밸런서를 생성하여 외부에서 Service에 접근 가능 (외부의 로드밸런서를 활용, 외부에서 접속할 수 있도록 연결)

`selector`
- `Service`가 트래픽을 전달할 `Pod`를 선택하는 기준. 여기서는 `app: backend-app` 레이블을 가진 Pod와 연결됨.

`ports`
- `protocol`: 접속 프로토콜 (`TCP/UDP`)
- `port`: 쿠버네티스 내부에서 Service가 노출하는 포트
- `targetPort`: 실제 Pod가 사용하는 포트
- `nodePort`: 외부에서 사용자들이 접근하게 될 포트 번호