# Lab - 練習 Health Check 和 Resource Quota

## 練習步驟

1. 練習在 Pod 新增 Health Check 設定

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
          - name: nginx-port
          containerPort: 80
        livenessProbe:
          httpGet:
            path: /
            port: nginx-port
          initialDelaySeconds: 15
          periodSeconds: 15
          timeoutSeconds: 30
          successThreshold: 1
          failureThreshold: 3
    ```

1. 練習在 Pod 新增系統資源限制

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
          - name: nginx-port
            containerPort: 80
        livenessProbe:
          httpGet:
            path: /
            port: nginx-port
          initialDelaySeconds: 15
          periodSeconds: 15
          timeoutSeconds: 30
          successThreshold: 1
          failureThreshold: 3
        resources:
          requests:
            memory: 64Mi
            cpu: 250m
          limits:
            memory: 128Mi
            cpu: 500m
    ```

1. 啟動 nginx-pod

    ```
    kubectl apply -f pod.yml
    ```

1. 檢查 Pod 細節

    ```
    kubectl describe pods nginx-pod
    ```

1. 關閉並移除容器

    ```
    kubectl delete -f pod.yml
    ```

