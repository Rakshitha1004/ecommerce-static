To install kubernetes K3s:
  curl -sfL https://get.k3s.io | sh -


Deployment.yaml :

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
        image: your-dockerhub-username/ecommerce:v1

        ports:
        - containerPort: 80




service.yaml :

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
