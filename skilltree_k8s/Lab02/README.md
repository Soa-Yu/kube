# Lab - 練習執行 Pod

## 練習步驟

1. 撰寫 Pod 設定, 建立 pod.yml

    ```yml
    apiVersion: v1
    kind: Pod
    metadata:
      name: nginx-pod
    spec:
    containers:
      - name: nginx
        image: nginx
        ports:
          - containerPort: 80
    ```

1. 透過 pod.yml 建立 Pod

    ```bash
    kubectl apply -f pod.yml
    ```

1. 檢查 Pod 建立狀態

    ```
    kubectl get pods
    ```

1. 檢查 Pod 細節

    ```
    kubectl describe pods nginx-pod
    ```

1. 移除 Pod

    ```
    kubectl delete pods nginx-pod
    ```