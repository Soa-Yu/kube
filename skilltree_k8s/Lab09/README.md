# Lab - 練習使用 Config Map

## 練習步驟

1. 建立 configMap

  ```
  kubectl create configmap app-config --from-file=application.yml
  ```


1. 掛載 Config Map 到 Pod 之中

    ```yml
    kind: Pod
    apiVersion: v1
    metadata:
      name: alpine
    spec:
      containers:
        - name: alpine
          image: alpine
          command: ["sleep", "3600"]
          volumeMounts:
            - mountPath: /data
              name: app-config
              readOnly: true
    volumes:
      - name: app-config
        configMap:
          name: app-config
    ```

1. 啟動服務

    ```
    kubectl apply -f .
    ```

1. 進入 Pod

    ```
    kubectl exec -it alpine -- sh
    ```

1. 查看是否有載入 Config

    ```
    cd /data && cat application.yml
    ```

1. 刪除 Pod

    ```
    kubectl delete -f pod.yml
    kubectl delete configmap app-config
    ```