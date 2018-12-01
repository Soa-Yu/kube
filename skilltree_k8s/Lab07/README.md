# Lab - 練習使用 Volume

## 練習步驟

1. 建立有 Volume 的 Pod

    ```yml
    kind: Pod
    apiVersion: v1
    metadata:
      name: alpine
    spec:
      containers:
        - name: alpine
          image: alpine
          command: ['sleep', '3600']
          volumeMounts:
            - mountPath: /data
              name: data-volume
      volumes:
        - name: data-volume
          hostPath:
            path: /tmp/data
            type: DirectoryOrCreate
    ```

1. 啟動服務

    ```
    kubectl apply -f .
    ```

1. 進入 Pod

    ```
    kubectl exec -it alpine -- sh
    ```

1. 嘗試建立檔案

    ```
    cd /data
    touch test.txt
    ```

1. 離開 Pod

    ```
    exit
    ```

1. 刪除 Pod

    ```
    kubectl delete -f .
    ```

1. 重新建立服務

    ```
    kubectl apply -f .
    ```

1. 查看檔案是否還在

1. 刪除 Pod

    ```
    kubectl delete -f .
    ```