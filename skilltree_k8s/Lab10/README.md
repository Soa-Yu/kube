# Lab - 練習使用 Namespace

## 練習步驟

1. 建立 Namespace

    ```yml
    apiVersion: v1
    kind: Namespace
    metadata:
      name: staging
    ```

1. 在 namespace 執行 deployment

    ```yml
    apiVersion: v1
    kind: Pod
    metadata:
      name: nginx-pod
      namespace: staging
    spec:
      containers:
        - name: nginx
          image: nginx
          ports:
            - name: nginx-port
              containerPort: 80
    ```

1. 查看 namespace 資源

    ```
    kubectl get pod --namespace staging
    ```

1. 設定 Namespace Resource

    ```yml
    apiVersion: v1
    kind: ResourceQuota
    metadata:
      name: compute-quotas
      namespace: staging
    spec:
      hard:
        limits.cpu: "1"
        limits.memory: 10Gi
    ```

1. 清除資源

    ```
    kubectl delete -f .
    ```