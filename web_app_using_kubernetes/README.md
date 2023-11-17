# Containerize Simple Web Page Using Docker

containerize a simple html page and deploy it on a Kubernetes Cluster on localhost.

## Getting started

Before starting, you will need to check the Docker is running on our machine or not.

     sudo systemctl status docker

## Step-1:

- first create a directory for this project and next, change the directory to your project:

  ```bash
      mkdir web_app_using_kubernetes
      cd web_app_using_kubernetes
  ```

- <i><b> NOTE :- First of all you can copy the above file content with respected names or you can download those files</b></i>  

- build docker image
  ```bash
      docker build -t index-web .
  ```
- To check whether you have created the image, use below command and inspect.
  ```bash
      docker images
  ```
- To run the html container server
  ```bash
      docker run -d -p 80:80 index-web:latest
  ```
- Now, you should be able to see the web page by searching for “localhost:80” in the web browser.  
  ![Alt text](image-2.png)

- To Inspect the containers running in the system

```bash
    docker ps
```

# Deploying The Containerized Application In Kubernetes Cluster On localhost.

we have written all the required yaml files. Let’s deploy this in the K8 cluster.

- Create the deployment using the below command.
  ```bash
      kubectl create -f index-web-deployment.yaml
  ```
- Create service using the below command
  ```bash
      kubectl create -f index-web-service.yaml
  ```
- Create Issuer and the Certificate using the below command.

  ```bash
      kubectl create -f index-web-issuer.yaml

      kubectl create -f index-web-certificate.yaml
  ```

- Create the ingress using the below command
  ```bash
      kubectl create -f index-web-ingress.yaml

  ```
- List all resources

  ```bash
      kubectl get all
  ```

- Now, you should be able to access the web page by

localhost:80<br> or <br>
0.0.0.0:80
![Alt text](image-2.png)


- Conclusion:- A Kubernetes Deployment tells Kubernetes how to create or modify instances of the pods that hold a containerized application like above app.

---------------------------THANK YOU---------------------------
