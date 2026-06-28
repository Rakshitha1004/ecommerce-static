# Kubernetes (K3s) Deployment

---

## Install Kubernetes (K3s)

Run the following command to install K3s on your Linux server:

```bash
curl -sfL https://get.k3s.io | sh -
```

---

## deployment.yaml

```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: ecommerce-deployment

spec:
  replicas: 2

  selector:
    matchLabels:
      app: ecommerce

  template:
    metadata:
      labels:
        app: ecommerce

    spec:
      containers:
      - name: ecommerce-container
        image: rakshithamr10/ecommerce:v1

        ports:
        - containerPort: 80
```

---

## service.yaml

```yaml
apiVersion: v1
kind: Service

metadata:
  name: ecommerce-service

spec:
  selector:
    app: ecommerce

  type: NodePort

  ports:
  - port: 80
    targetPort: 80
    nodePort: 30080
```
