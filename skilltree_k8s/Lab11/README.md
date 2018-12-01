# Lab - 練習使用 Ingress

## 練習步驟

1. 建立 Ingress

    ```yml
    apiVersion: extensions/v1beta1
    kind: Ingress
    metadata:
      name: app-ingress
      namespace: default
    spec:
      rules:
        - http:
            paths:
              - path: /
                backend:
                  serviceName: app-service
                  servicePort: 8080
    ```

1. 啟動服務

    ```
    kubectl apply -f .
    ```

1. 使用瀏覽器開啟網頁

1. 清除資源

    ```
    kubectl delete -f .
    ```