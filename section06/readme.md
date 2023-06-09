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
