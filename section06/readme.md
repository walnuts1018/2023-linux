# 第6回コピペコマンド

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

### nginx-test-loadbalancerのdeploymentを作る

```bash
kubectl create deployment nginx-test-loadbalancer --image=nginx:latest -- 'sed -i 13i"<p style=\"font-size: 30px; color: red;\">This is $HOSTNAME pod</p>" /usr/share/nginx/html/index.html && nginx -g "daemon off;"'
```

```
sed -i 13i"<p style=\"font-size: 30px; color: red;\">This is $HOSTNAME pod</p>" /usr/share/nginx/html/index.html && nginx -g "daemon off;"
```
