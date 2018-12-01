# Lab - 練習部署策略

## 練習步驟

1. 設定更新策略

    ```yml
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: app-deployment
    spec:
      replicas: 3
      strategy:
        type: RollingUpdate
        rollingUpdate:
          maxSurge: 25%
          maxUnavailable: 25%
      selector:
        matchLabels:
          app: app-deployment
      template:
        metadata:
          labels:
            app: app-deployment
        spec:
          containers:
            - name: app
              image: kirkchen/version:1.0.0
              ports:
                - containerPort: 80
    ```

1. 啟動服務

    ```
    kubectl apply -f .
    ```

1. 升級 Image 版本

    ```
    kubectl set image deploy/app-deployment app=kirkchen/version:2.0.0
    ```

1. 查詢 rollout 狀況

    ```
    kubectl rollout status deploy app-deployment
    ```
  
1. 清除容器

    ```
    kubectl delete -f ./
    ```