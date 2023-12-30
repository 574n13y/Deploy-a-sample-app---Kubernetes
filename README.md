# Deploy-a-sample-app---Kubernetes
 - Write Kubernetes yaml file to deploy a sample app (You can use any publicly available app as deployment image) &amp; make sure:
    a. App is highly available.
    b. App/Pods can be updated in rollout manner.

- Signup to [killercode](https://killercoda.com/login)
- Login to Killercode
  ![kllrcode](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/38c3b15b-ffb4-4951-ae80-942b98b9e98a)

- install docker if not installed already
- open vi write a kubernetes file.
  ```
  yaml
  # deployment.yaml

  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: sample-app
  spec:
    replicas: 3  # Adjust the number of replicas based on your high availability requirements
    selector:
      matchLabels:
        app: sample-app
    template:
      metadata:
        labels:
          app: sample-app
       spec:
         containers:
          - name: sample-app
          image: nginx:latest  # Replace with your desired publicly available app image
          ports:
          - containerPort: 80
     strategy:
       rollingUpdate:
         maxSurge: 1
         maxUnavailable: 1
         type: RollingUpdate

  ```
 ![Screenshot 2023-12-30 142721](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/ac0eda5e-0a4a-4078-9e4a-126e7db0526b)
 ![Screenshot 2023-12-30 143144](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/3716a301-3e2f-4d33-8fa5-b8c875283a30)
 ![Screenshot 2023-12-30 143215](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/05e27a46-f37b-468f-af90-7c93e8eb300c)

  ```
   apt-get update
   kubectl get nodes
   kubectl version
  ```

- This YAML file defines a Kubernetes Deployment with three replicas, ensuring high availability. The rollingUpdate strategy ensures that during a deployment update, only one new pod is created at a time (maxSurge: 1), and at least one old pod is available (maxUnavailable: 1), making the update process gradual and minimizing downtime.
- Make sure to replace nginx:latest with the actual image of the publicly available app you want to deploy.
- Apply the YAML file using the kubectl apply command:
  ```
  # bash
    kubectl apply -f deployment.yaml
  ```
- This will create the deployment and the necessary pods for your sample app, ensuring high availability and supporting rolling updates.
  ![view kube details](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/b4492b33-f2dc-43f4-a55f-0dc0f9dcbd34)

- deployments detail
  ```
   kubectl get deployments
  ```
  ![get deployment](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/78aa0619-560b-456f-bebe-b619c9c5b58c)

- get nodes
  ```
  kubectl get nodes
  ```
 ![get nodes](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/4073f18c-21ac-48a6-9460-b362864d854e)

- describe deployment sample-app
  ```
   kubectl describe deployment sample-app
  ```
  ![describe deployment](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/506e0cf5-1d48-414b-9c10-2c665c44a9b7)

- describe pods
  ```
  kubectl describe pods
  ```
  ![describe pods](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/be22b363-8243-4749-9654-ba1da4176c0f)
  ![describe pods 1](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/3805412f-8527-42d0-aba6-4ea99a1e8979)
  ![describe pods 2](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/eacd135f-3922-49db-a0ba-6bf61578a3a8)

- describe pod and app
  ```
  kubectl get pods -l app=sample-app
  ```
  
- describe pod apps 1,2,3
  ```
  kubectl describe pod sample-app-587d9c6687-2gk8r
  ```
  ![pod 1](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/cea33bc4-c9b5-47a8-a284-3d55f132b745)

  ```
  kubectl describe pod sample-app-587d9c6687-7cgft
  ```
  ![pod 2](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/af2e5040-9cf1-4eb6-9024-46e622176e98)

  ```
  kubectl describe pod sample-app-587d9c6687-cxz4h
  ```
  ![pod 3](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/76982ab3-190a-440b-b291-34a384e9cffb)

- get pod app details
  ![get nodes](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/0e53617e-c5df-4165-989d-2c3892f9cbb7)
  
- delete deployment
  ![delete](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/a5b9597b-91b2-4e24-86ac-0cb35a3d9289)


##  Deploy-a-sample-app via MiniKube on GCP 

 - All the above process is same part from installation
 -  install docker & minikube
   ![1](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/021601f1-4b48-4b41-9289-52c61e157177)
   ![2](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/836809e8-0f56-45c8-8049-59b270092f8a)
   ![3](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/99db0725-e5e4-46aa-b3d9-32eef69c363b)
   ![4](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/3dd22bd3-e2fe-466b-82ad-f5f39d7438d7)
   [5](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/924bf378-3884-4959-9d24-09cb3997f134)
   ![6](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/34ce2da8-6197-4dc8-9a25-b216f2bca5ae)
   ![7](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/8c86fa00-ee8b-4ffa-841e-c0d759cb6127)
   ![8](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/65bd5e95-5a40-410b-9f19-2b30fa12634f)
   ![9](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/77f06356-d9c0-44cd-bd04-050c0465e00e)
   ![10](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/9948484b-a939-41d0-9c7f-24d62370698e)
   ![11](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/58b9ccf3-d8c9-40f2-b3d3-2ec049538437)
   ![12](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/c8f37f2b-9916-4a01-99b7-e087cdd24525)
   ![13](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/e07e33fe-e967-4603-b474-e844b57104c7)
   ![14](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/49537c3c-53fe-4286-97a1-f2b5bd340c0e)
   ![15](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/f195f84c-a1b5-4026-893b-cde180a5e475)
   ![16](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/76a09c0d-0e1f-4273-b442-b7d17126c74e)
   ![17](https://github.com/574n13y/Deploy-a-sample-app---Kubernetes/assets/35293085/48c75a58-86a0-4fb4-9495-6716e0559767)










 

 


                                                ****
