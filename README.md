![logo image](readme-pics/Reverse-Brand-LogoWithText.png)

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 12.2.8. 

## Description 
Reverse is an emergent social media application that helps Revature employees connect with their colleagues inside - and outside - of the workplace. Employees can create and customize their profiles, showcasing the professional achievements they'd like to celebrate with their peers via textual and visual posts. They can also encourage and advise their colleagues by "liking" and commenting on various posts as they appear in their curated Reverse news feeds.

## Technologies 
 - HTML5
 - CSS 
 - SCSS
 - Angular Material UI
 - TypeScript
 - Angular
 - Angular CLI  
 - Node.js
 - Dockerfile
 
## Components
### HomepageComponent 
-> This component contains the home page: the first thing the user sees on the site
![homepage](readme-pics/homepage-before-login.JPG)
This is the home page before logging in. The user has to regiser and log in before using the service. 

![homepageafterlogin](https://user-images.githubusercontent.com/8985349/141241140-a69e8287-236a-48ce-b3d1-0cb5427e0f18.png)
This is the home page after logging in.


### LoginRegisterComponent
-> This component provides a double tabbed form for the user to register and log in in the html template. We styled in with a galaxy background-image with color overlay.Images were used in the clickable tabled with a Revature graphic.
![registration](readme-pics/registration-form.JPG)

### UserComponent
--> Displays to the logged-in user their posts and related users and the navigation sidebar to edit their profile or add posts or like posts
![userprofilecomponent](https://user-images.githubusercontent.com/8985349/141241504-daa05dcf-50fd-4d25-b92b-48c69f28d778.png)

### UserProfileEditComponent
-> This allows users to edit their profile or information.
![userprofileeditcomponent](https://user-images.githubusercontent.com/8985349/141241619-46a9b299-74b3-4378-8474-fe79cdd07e6b.png)

### PostComponent & AddPostComponent
-> This component gives the ability to create and submit verses (posts), to like verses, and to create comments for these posts. 
![fullpostcomponent](https://user-images.githubusercontent.com/8985349/141241490-2abf1bbc-94a2-4568-8dcc-bf3b62c31e79.png)
This is the PostComponent

![newpostcomponent](https://user-images.githubusercontent.com/8985349/141241377-4c2c6e32-938a-4543-99aa-c92d345b705b.png)
This is the AddPostComponent

### HeaderComponent
-> This provides the universal header with the search feature at the top of every component, the header for every page. 
![headercomponent](https://user-images.githubusercontent.com/8985349/141241074-d352836a-f78e-4dcf-9df3-b8e5e3631297.png)

### SidebarComponent
-> This provides the side-bar for navigating the site after logging in. 
![sidebarcomponent](https://user-images.githubusercontent.com/8985349/141241657-4f67cea9-f8fe-46fe-97dd-c5a61aed1f26.png)


### EditPostComponent
-> This allows users to edit their posts in case they want to erase any profanity which their is a filter for.
![editpostcomponent](https://user-images.githubusercontent.com/8985349/141241001-350c2bb0-558f-4611-b6b7-2aa9ee08c29e.png)


## Interceptors 
### LoadingScreenInterceptor 
-> Used to implement the loadding screen by intercepting Http requests and using the LoadingScreenService execute the loading screen when transitioning between component screens. 

### TokenInterceptor 
-> Used to intercept the Http Request to grab the JWT token for authentication and maintaining a log-in session 

## Getting Started
- git clone https://github.com/Revature-Reverse/Reverse-Angular.git and move into its folder
- If you are using a Windows terminal, consider running "Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass" to be to run scripts
- Run `npm install -g @angular/cli` to install the Angular CLI
- Run `npm install` to install all dependencies. 
- Run `ng new project_name` to start a new project. 
- Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.
- Create a new folder for the Discovery repo, move into this folder, and run `git clone https://github.com/Revature-Reverse/Discovery.git`
- Create a new folder for Gateway repo, move into this folder, and run `git clone https://github.com/Revature-Reverse/Gateway.git`
- Create a new folder for User-Service repo, move into this folder, and run `git clone https://github.com/Revature-Reverse/User-Service.git`
- Create a new folder for Post-Service repo, move into this folder, and run `git clone https://github.com/Revature-Reverse/Post-Service.git`
- Open your favored IDE and run the Discovery, GateWay, User-Service, and Post-Service (in this order)


# Discovery

In order for your service to be discoverable, it needs some YAML.

You need to have a name for the discovery service to expose to the gateway.
spring:
application:
name: your-service-name-as-you-want-it-to-appear //(should be user-service or post-service for now)

You need to point your service in the direction of the discovery service itself so it can register itself.
Please note that the discovery service will be running on the same machine as yours (for now), so (for now) you
should not use port 8083 yourself.
eureka:
client:
serviceUrl:
defaultZone: ${EUREKA_URI:http://localhost:8083/eureka} //Environment variable with default

You can, in fact, allow Eureka to determine the port that your service uses by setting the port to 0.
server:
port: 0

## Installation

Clone https://github.com/Revature-Reverse/Discovery.git, open the project in your IDE, and run it.


# Gateway

This is a minimally configured Spring Cloud Gateway. It currently points /users and /lists to a User-Service and /posts and /comments to a Post-Service. You will need to update it if you want to add new services, routes, or more advanced features like circuit-breaking.

To run the gateway, clone https://github.com/Revature-Reverse/Gateway.git, open it in the IDE of your choice, and run the project.


# Post Service

## Overview

Post Service is responsible for handling posts and related content, including images. It handles the things that a user _does_, including the CRUD of posts, but also the modification of post meta-data such as likes. Requests made to the Post Service are authenticated by a call to User Service validation.

## Technologies

- Java
- Spring Boot
- Spring Web
- Spring WebFlux
- Spring Data JPA
- Log4J
- Netflix Eureka
- JUnit4
- Mockito
- Lombok
- Hibernate

## Getting Started with Post-Service

1. Install and run Discovery (unless you want to temporarily disable self-registration by modifying the YAML config and removing the Eureka dependency in the POM)

2. Install and run Gateway (technically optional, but recommended to avoid manually setting location of services)

3. Install and run User-Service (unless you want to temporarily remove JWT validation as that requires the user-service be up)

4. Clone repo from https://github.com/Revature-Reverse/Post-Service.git

5. Open in IDE of your choice

6. Set environment variables:

DB_USERNAME is the username for your user on your database

DB_URL is the address of your database with the appropriate prefix (jdbc:postgresql://reverse.xxxxxxx.us-east-1.rds.amazonaws.com/postgres, for example)

DB_PASSWORD is the password for your user on your database

EUREKA_URI is the IP:port address of your Discovery service, this should be set in production but shouldn't need to be set for local testing

VALIDATION is the full address for accessing your USER-SERVICE validation endpoint (http://localhost:8084/users/validate if you are running vanilla Gateway/Discovery/User-Service/Post-Service locally)

AWS_ACCESS_KEY and AWS_SECRET_KEY are necessary to set up programmatic access to the S3 bucket for storing images.

7. Create run configuration with PostServiceApplication.java as the main class

8. Run


# Reverse Assets

This project contains documentation and assets used for the reverse project. Things like our logo, deployment files, examples, ect...

## Files

Bellow you will find the map of the files included in this repository.

- [GenerateSQLScripts](https://github.com/Revature-Reverse/Assets/tree/master/GenerateSQLScripts) - This contains the python code to generated the sql scripts that create our dummy data
- [Logos And Images](https://github.com/Revature-Reverse/Assets/tree/master/Logos%20And%20Images) - This contains out logos and other misc project iomages
  - [ZoomBackgrounds](https://github.com/Revature-Reverse/Assets/tree/master/Logos%20And%20Images/ZoomBackgrounds) - This contains some of the background we chould use for our zoom presentation
- [S3Example](https://github.com/Revature-Reverse/Assets/tree/master/S3Example) - This project has an example for how to do S3 file upload
- [traefik/config.d](https://github.com/Revature-Reverse/Assets/tree/master/traefik/config.d) - This is where you can put any extended configuration for traefik
- [DatabaseERD.PNG](https://github.com/Revature-Reverse/Assets/blob/master/DatabaseERD.PNG) - Image of our database ERD
- [SETUP.md](https://github.com/Revature-Reverse/Assets/blob/master/SETUP.md) - Instructions for setting up the application in a production enviorment
- [README.md](https://github.com/Revature-Reverse/Assets/blob/master/README.md) - This file
- [docker-compose.yml](https://github.com/Revature-Reverse/Assets/blob/master/docker-compose.yml) - Docker compose file for running the application in production
- [example.env](https://github.com/Revature-Reverse/Assets/blob/master/example.env) - Example enviorment file for running the application in producstion
- [setup.sql](https://github.com/Revature-Reverse/Assets/blob/master/setup.sql) - File to create the database tables and some dummy data
- [traefik.yml](https://github.com/Revature-Reverse/Assets/blob/master/traefik.yml) - Overall traefik configuration

# DevOps

## Pipeline

## Monitoring
Install grafana onto the K8s cluster.
 - PersistentVolumeClaim
 - Deployment
 - Service

Install loki using helm
 - helm repo add loki https://grafana.github.io/loki/charts
 - helm repo update
 - helm upgrade --install loki loki/loki-stack

Open Grafana at http://Grafana-node-IP:3000/login
 - Default Username/Password (admin/admin)

Add Loki as a data source
 - URL is http://loki:3100

Verify logs are accessible by Grafana
 - Click Explore on the taskbar to the left of the screen. (The symbol is a compass)
 - Click Log browser, select app, select reverse-angular-api, post-service-api, and user-service-api.
 - Select show logs

Install prometheus using helm
 - helm repo add bitnami https://charts.bitnami.com/bitnami
 - helm repo update
 - helm install prometheus bitnami/kube-prometheus

Verify prometheus is monitoring the User-service and Post-service
 - Run kubectl port-forward --namespace default svc/prometheus-kube-prometheus-prometheus 9090:9090
 - Go to http://localhost:9090/targets and ensure you see the 'user-service-monitor' and 'post-service-monitor' in the list of All targets

Add Prometheus as a data source
 - URL is http://prometheus-kube-prometheus-prometheus.default.svc.cluster.local:9090/

Create dashboards for your needs
 - Create dashboard
 - Add a panel for each of the logs so you can trace anything done
 - Import the JVM (Micrometer) dashboard for prometheus
   - Use code 4701

## Kubernetes

Create Regional Cluster and SQL instance within GCP. It is ideal to have multiple regional master nodes as well as worker nodes to protect against zonal failure.

AWS Bucket & Credentials needed for Post-Service API.

Package APIs (Reverse-Angular, Post-Service, User-Service) and build and push these images to Docker.

Pull and create basic deployments for the following images with access to the following environmental variables:
 - javasre2022/angular:latest
    - VALIDATION 
    - EUREKA_URI
    - ANGULAR_URI
 - javasre2022/postservice:latest
    - VALIDATION
    - EUREKA_URI
    - ANGULAR_URI
    - AWS_ACCESS_KEY
    - AWS_SECRET_KEY
 - javasre2022/userservice:latest ***NOTE - ALSO NEEDS A PERSISTENTVOLUME / PERSISTENTVOLUMECLAIM***
    - VALIDATION
    - EUREKA_URI
    - ANGULAR_URI
    - AWS_ACCESS_KEY
    - AWS_SECRET_KEY
    
Create services for each deployment above, where all three will also act as load balancers.

Install Jenkins Pipeline and Grafana on the cluster. Note: Due to us not being able to access the GCP services we requried, we setup ClusterRoleBindings to get Jenkins working properly.


