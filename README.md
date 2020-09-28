# Deploy Go Application on Kubernates Cluster 
- this repo contains: 
 1. docker file to build docker image 
 2. helm chart to deploy the application on kubernates cluster 
 3. Go  Hello World applicaiotn 
 4. kubernates deployment file for the app.
 5. kubernates service file 

#### clone this repo :
    ```git clone https://github.com/aboubakrkh/go-kubernates.git```

#### the Repo architecture is as following: 

├── docker

│   ├── Dockerfile

│   └── main.go

└── go-helm-chart

    ├── Chart.yaml
    
    ├── templates
    
    │   ├── go-kube.yml
    
    │   └── service.yml
    
    └── values.yaml
    
  #### to run the application directly please do the following: 
   - after cloning the repo:
      - ```cd go-kubernates/go-helm-chart```
      - ```helm install go-kube .``` 
      - the application runs on port 31008 and you can change it from values.yaml 
      - ```curl clusterip:31008``` you should able to see Hello World
      
    
###### Building docker Image

  - to build the Docker Image please run the below command : --> in case using public repo like dockerhub .
    - ```cd go-kubernates/docker``` 
    - ``docker build -t dockerhubname/imagename:tag .``  --> you need to specify a valid dockerhub account to be able to push the image 
    - in my case i used : ``docker build -t aboubakr/go-kube:latest .``
    - you can test the image by creating a new container like:
        - ```docker run -it -p 8010:8080 aboubakr/go-kube:latest``` 
        - ```curl localhost:8010``` you sould be able to see: 
                Hello World
    - ``docker login`` 
      - provide you username and password for dockerhub 
    - ``docker push aboubakr/go-kube:latest``
### to deploy this application on kubernates
  - after pushing docker image to your dockerhub or you private repo 
  - ```cd go-helm-chart```
  - change replace the image name with the image that you created 
  - inside go-helm-chart run :
    - ``` helm install go-kube . ``` 
    - this will deploy the application and a service to expose the app.
  - the application runs on port 31008 and you can change it from values.yaml 
  - ```curl clusterip:31008``` you should able to see Hello World
    
    
    
    
    
    
