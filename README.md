# ThoughtWorks
## Assigment
Automate Mediawiki App Deployment using Kubernetes with Helm chart.Here, there are tools required are Kubernetes with internet access to pull images from docker hub and Helm 3 installed on machines from where you are running this helm chart.
deployment involves: 1. Kubernetes 2. External IP (Access App) 3. Helm 3 
1. Git clone the repo in order to setup deployment. 
2. Make sure that you have access to the kubernetes cluster and cluster resources in order to deploy applications.
3. Make sure that you have helm3 installed on your machine where you have cloned the git repo.
Helm chart contains deployment of application and DB, service for app and DB, secret for DB, persistent volume for storing data. All the variables will get in values.yaml. For deploying this application I have used docker images of mediawiki and mariadb, which is available from hub.docker.com and hence for the time being I have pointed it to the latest tag. However if you need some other image tag you can set in values.yaml or can pass at the installation of helm chart.

helm commands

To check the deployed application you can check with

Please make sure that you have copied the public IP from mediawikisvc in order to set up the application.Please paste this Public IP in the browser and configure the application. At the database configuration page you need to add host as databasesvc username:  password: continue. Rest feel the details and application will be done with installation.

If you need to do CI/CD for the same, you can use this helm chart as for doing CI/CD by updating the changes in values.yaml and can be deployed in clusters.For  sake, currently I have set replicas = 1 as min. if needed to scale then can be changed  and scale app and DB.  Currently I have not set any ingress or hpa to scale the application, if needed that can be set and configured. 
