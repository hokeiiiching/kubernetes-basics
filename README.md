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