# Lab - 練習使用 Secret

## 練習步驟

1. 建立 secret.yml

    ```yml
    apiVersion: v1
    kind: Secret
    metadata:
      name: app-account
    type: Opaque
    data:
      username: c2tpbGx0cmVlCg==
      password: MjAxODEyMDEK
    ```

1. 掛載 Secret 到 Pod 之中

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
              name: app-account
              readOnly: true
    volumes:
      - name: app-account
        secret:
          secretName: app-account
    ```

1. 啟動服務

    ```
    kubectl apply -f .
    ```

1. 進入 Pod

    ```
    kubectl exec -it alpine -- sh
    ```

1. 查看是否有載入 Secret

    ```
    cd /data && ls
    ```

1. 刪除 Pod

    ```
    kubectl delete -f .
    ```