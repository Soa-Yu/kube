# Lab - 練習查看 Pod 狀態

## 練習步驟

1. 啟動 nginx-pod

    ```
    kubectl apply -f pod.yml
    ```

1. 把 nginx 的 port mapping 到本地端

    ```
    kubectl port-forward nginx-pod 80:8080
    ```

1. 使用瀏覽器開啟 http://localhost:8080 看看是否有成功

1. 練習進入 Pod

    ```
    kubectl exec -it nginx-pod -c nginx -- sh
    ```

1. 練習查看容器內容狀態

1. 關閉並移除容器

    ```
    kubectl delete -f pod.yml
    ```

