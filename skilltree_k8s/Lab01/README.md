# Lab - 練習執行 k8s 應用程式

## 練習步驟

1. 執行 hello-world

    ```
    kubectl run hello --image=crccheck/hello-world --port=8000
    ```

1. 開放外部使用 NodePort 存取 hello-world 

    ```
    kubectl expose deployment hello --type=NodePort
    ```

1. 取得 hello-world 網址

    ```
    minikube service hello --url
    ```

1. 使用瀏覽器開啟網址