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
