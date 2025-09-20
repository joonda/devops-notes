### Pod

- create manifest file
- `kubectl apply -f [manifest file]`
```shell
kubectl apply -f nginx-pod.yaml
```

- search pod list
```shell
kubectl get pods
```

- pod port-forwarding
- `kubectl port-forward pod/[pod name] [local port]:[container port]`
```shell
kubectl port-forward pod/nginx-pod 80:80
```

- delete pod
- `kubectl delete pod [pod name]`
```shell
kubectl delete pod nginx-pod
```

- search pod detail
- `kubectl describe pod [pod name]`
```shell
kubectl describe pod nginx-pod
```

- check pod logs
- `kubectl logs [pod name]`
```shell
kubectl logs nginx-pod
```

- exec into pod
- `kubectl exec -it [pod name] -- [bash]`
- `kubectl exec -it [pod name] -- [sh]`
```shell
kubectl exec -it nginx-pod -- bash
```