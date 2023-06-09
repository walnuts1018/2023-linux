# 第6回コピペコマンド

## Tips

```bash
kubectl completion powershell | Out-String | Invoke-Expression
```

## 前回の補足

### 前回のServiceを消す

```bash
kubectl delete service nginx-test
```

### Serviceを作る

```bash
kubectl expose deploy nginx-test --type=NodePort --port 80 --target-port 80
```

## LoadBalancerを使ってみる

```bash
minikube addons enable metallb
```

```bash
kubectl apply -f https://raw.githubusercontent.com/walnuts1018/2023-linux/main/section06/metallb-configmap.yaml
```

### nginx-test-loadbalancerのdeploymentを作る

```bash
kubectl apply -f https://raw.githubusercontent.com/walnuts1018/2023-linux/main/section06/nginx-test-LB-deployment.yaml
```

```bash
kubectl expose deploy nginx-test-loadbalancer  --type=LoadBalancer --port 80 --target-port 80
```

## DeploymentとReplicasetとPod

### Pod

```bash
kubectl apply -f ./nginx-test-pod.yaml
```

### Replicaset

```bash
kubectl apply -f ./nginx-test-replicaset.yaml
kubectl get replicaset,pod 
```

### Deployment

```bash
kubectl apply -f./nginx-test-deployment.yaml
kubectl get deploy,replicaset,pod 
```

### Rolling Update

```bash
kubectl apply –f ./nginx-test-deployment.yaml
```

```bash
kubectl get pod -w
```

### describe

```bash
kubectl describe pod nginx-test3-xxxxxxx-yyyyyyy
```

### Rollout履歴

```bash
kubectl rollout history deployment nginx-test3
```

```bash
kubectl rollout history deployment nginx-test3 --revision=1
kubectl rollout history deployment nginx-test3 --revision=2
```

### Rollback

```bash
kubectl rollout undo deployment nginx-test3
```

```bash
kubectl rollout undo deployment nginx-test3　--to-revesion=2
```
