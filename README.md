# Kaiburr Task 2
## Deployment of the Spring Boot Application using Kubernetes

### Pre-requisites 
Ensure that Minikube, Docker-Desktop, Postman, and MongoDB Compass are installed in the system. 


### About the project
&emsp;1. Use git clone https://github.com/M-JB413/KaiburrTask2.git to download the files locally.  
&emsp;2. cd into the TasksLocal Directory.  
&emsp;3. The directory has the source code of the spring boot application. All the .yaml configuration files are placed inside `TasksLocal\src\main\resources`  
&emsp;4. The database configurations are inside the `application.yaml` file.  
&emsp;5. The project uses the `admin` database inside MongoDB. To use a different database add the following changes to the `application.yaml` file inside `spring.data.mongodb`.  
&emsp;&emsp;i) In `spring.data.mongodb.database` give the desired `database-name`.  
&emsp;&emsp;ii) Add a new field: `spring.data.mongodb.authentication-database` and value: `admin`  
&emsp;6. Make sure that the credentials and other configurations are properly set in the `.yaml` files.  
&emsp;7. Once set, build a JAR file, dockerize it, and push the image to docker hub.  
&emsp;8. Set up the Kubernetes cluster and deploy each `.yaml` file using `kubectl apply -f [file-name]`.

### About the YAML configuration files and order of deployment
&emsp;1. `volume.yaml` -> Creates a persistent volume of stateful services. **Note:** Before creating Persistent Volume make sure you create the following directory: `/storage/data` inside minikube node.  
&emsp;2. `mongosecret.yaml and mongoconfig.yaml` -> Files that have the authentication credentials and other configuration parameters.  
&emsp;3. `mongodb.yaml` -> Contains both the Deployment component and Service component.  
&emsp;4. `springdeploy.yaml` -> Contains PersistentVolumeClaim, Deployment and Service component.  
&emsp;5. To log and inspect the pods use commands: `kubectl describe pod [pod-name] and kubectl logs [pod-name]`.  

### Screenshots

#### Setting up Minikube
![Minikube setup](https://github.com/M-JB413/KaiburrTask2/assets/83492132/0d51ab57-3e8f-4849-8fb8-031eb2681eba)


#### PersistentVolume Creation
![Persistent Volume Setup](https://github.com/M-JB413/KaiburrTask2/assets/83492132/64e54664-f61c-4de9-990a-d1d91b55a8dc)


#### Creating Secrets
![MongoDB Secrets](https://github.com/M-JB413/KaiburrTask2/assets/83492132/19b0f2f0-2b0c-49cb-b773-d2ed5713cad0)


#### Deploying MongoDB
![MongoDB Deployment](https://github.com/M-JB413/KaiburrTask2/assets/83492132/fccd57c2-f43e-4bd0-a481-8d7f48d0e333)


#### MongoDB Pod connection from host system using MongoDB Compass
![MongoDB Connection from Host](https://github.com/M-JB413/KaiburrTask2/assets/83492132/53c22108-bbff-4811-9b55-c8b00f7fcbd6)


#### Build docker image for spring application
![SpringBoot Docker Build](https://github.com/M-JB413/KaiburrTask2/assets/83492132/92f71c8a-1cb8-43e4-a787-5c7d78d572a7)


#### Deploy SpringBoot Application (Make sure ConfigMap is created)
![SpringBoot Deploy](https://github.com/M-JB413/KaiburrTask2/assets/83492132/e9f8e91c-fb1b-4477-9fa6-30440b988899)


#### Running of Spring Application
![SpringBoot Application Running](https://github.com/M-JB413/KaiburrTask2/assets/83492132/f06016b0-7879-4db6-b586-74e9433a4228)


#### SpringBoot Pod connection from host system using Postman
![SpringBoot Connection from Host](https://github.com/M-JB413/KaiburrTask2/assets/83492132/5f7683e4-f808-4b07-9196-1c8252cc38c7)


#### Sample example of communication between Pods using POST Request
![Sample POST Data to Mongo using Spring](https://github.com/M-JB413/KaiburrTask2/assets/83492132/a9a6cf6a-6a11-4a2b-9000-f25dc4315d46)

