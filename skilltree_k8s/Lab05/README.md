# Lab - 練習建立 Deployment 和 Service

## 練習步驟

1. 建立 deploy.yml

    ```yml
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: app-deployment
    spec:
      replicas: 3
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

1. 建立 service.yml

    ```yml
    apiVersion: v1
    kind: Service
    metadata:
      name: app-service
    spec:
      ports:
      - port: 8080
        protocol: TCP
        targetPort: 80
      selector:
        app: app-deployment
    ```

1. 啟動服務

    ```
    kubectl apply -f .
    ```

1. 取得 minikube 存取 Service 的網址

    ```
    minikube service app-service --url
    ```

1. 清除 Pod

    ```
    kubectl delete -f ./
    ```