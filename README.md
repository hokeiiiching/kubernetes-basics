# Learning Kubernetes through a project-based tutorial
I was interested in learning more about container management and deploying applications,
so I decided to follow along a Kubernetes crash course that came with a project for practical learning experience.

Notes.md contains the notes that I took down while watching the lecture.


## Project Overview
I will be deploying a MongoDB Database and a Web Application. The web app will be connected to the database using a server with external configuration for DB URL and Credentials from ConfigMap and Secret.
I will make the web application accessible externally from the browser.


### K8s Components Overview
- 4 K8s Config Files 
    - ConfigMap with MongoDB endpoint
    - Secret with MongoDB User & Password
    - Deployment & Service with MongoDB Application with internal service
    - Deployment & Service of our own WebApp with external service 


### Learning Outcomes from project
#### Handling of Secret
In this project, I learnt to add my secret.yaml file to .gitignore (to prevent malicious access to the database's username and password). 

More importantly, I learnt how to use Sealed Secrets to encrypt the secret.yaml file. The sealedsecret.yaml that appears in the git repo is completely safe to be viewed by the public, as it is encrypted.

When I apply Sealed Secret to my cluster, the Sealed Secrets controller will decrypt it back into a regular Kubernetes Secret. This is done via:
kubectl apply -f sealedsecret.yaml