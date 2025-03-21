# Creating a project "my-docker-app"
## cd my-docker-app
## Install npm
![1](https://github.com/user-attachments/assets/a34e6736-031e-42ee-b751-e05455591881)
)
# Pull the docker image
## Build the image
![2](https://github.com/user-attachments/assets/97c8c7f6-8235-4ae2-9cd1-b2402694cd0f)
)
# Exit the project "my-docker-app" using cd ..
## Start the minikube
![9](https://github.com/user-attachments/assets/d8e217b7-1c7e-4f67-9bfd-bb067ca612e0)
)
)
# Open the file nginx-deployment.yaml
## paste the code
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 1
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app
        image: santhapriyan/docker:latest
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 80
```
# Also open service.yaml
## paste the code
```
apiVersion: v1
kind: Service
metadata:
  name: my-app
  namespace: default
spec:
  type: NodePort  # Ensures external access via a specific port
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80       # Service port inside the cluster
      targetPort: 80  # The container's port
      nodePort: 30391   # Externally accessible port
```
# Get pods using kubectl
![4](https://github.com/user-attachments/assets/31b77058-50ce-42dd-b9c3-a16f568f2f46)
)
# Get the url using minikube service
![5](https://github.com/user-attachments/assets/7d1b1d82-6c19-4944-bc6c-bda02ccbff10)
)
# Paste the url with using curl
![6](https://github.com/user-attachments/assets/df54dda4-c070-4218-b45c-75643ad1fde5)
)
# Open the url:http//192.168.2:30391
![7](https://github.com/user-attachments/assets/6328fc25-2c7f-4b75-9517-8a346fb7b466)
)

