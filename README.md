# ThoughtWorks
## Assigment
Automate Mediawiki App Deployment using Kubernetes with Helm chart. Here, there are tools required are Kubernetes with internet access to pull images from docker hub and Helm 3 installed on machines from where you are running this helm chart.
### Deployment involves: 
1. Kubernetes 2. External IP (Access App) 3. Helm 3 

### Steps:
1. Git clone the repo in order to setup deployment. 
2. Make sure that you have access to the kubernetes cluster and cluster resources in order to deploy applications.
3. Make sure that you have helm3 installed on your machine where you have cloned the git repo.

Helm chart contains deployment of application and DB, service for app and DB, secret for DB, persistent volume for storing data. 
All the variables will get in values.yaml. 
For deploying this application I have used docker images of mediawiki and mariadb, which are available from https://hub.docker.com/_/mariadb , https://hub.docker.com/_/mediawiki and hence for the time being I have pointed it to the latest tag. However if you need some other image tag you can set in values.yaml or can pass at the installation of helm chart.

### Following are the commands to install helm chart
1. Git Clone

```git clone https://github.com/apurvabhandari/ThoughtWorks.git```

2. Navigate to directory 

```cd ThoughtWorks/helm3/```

3. Check helm 3 version

```helm version```

helm version should be 3 and above

4. Install helm chart

```heml install mediawiki mediawiki-app/```

5. Check deployed chart

```helm list```


### To check the deployed application you can check with kubenetes command with cluster
1. Check application up and running

```kubectl get deployment```

```kubectl get pod```

2. Check service

```kubectl get svc```

#### Note: If you are deployed in GKE (Google Cloud) then please copy the Public IP of LoadBalancer for service mediawikisvc in order to access applications on the browser.

Now paste the Public IP in Browser and start browsing. You will get a mediawiki page. 
To configure the application till end I have configured this values in values.yaml
- Mariadb DB host as DB service name: databasesvc
- mysql database: my_wiki
- mysql_password: example
- mysql_user: wikiuser

Details:
- Please make sure that you have copied the public IP from mediawikisvc in order to set up the application. 
- Please paste this Public IP in the browser and configure the application. 
- At the database configuration page you need to add host as databasesvc and continue. 
- Rest feel the details and application will be done with installation.

### Application CI/CD:

If you need to do CI/CD for the same, you can use this helm chart as for doing CI/CD by updating the changes in values.yaml and can be deployed in clusters.
For  sake, currently I have set replicas = 1 as min. if needed to scale then can be changed  and scale app and DB.
In order to update the application you can do the changes in values.yaml, in image tag with AppVersion so if the new build image is ready then it can be easily deployed with helm upgrade.

### Application scaling:

Currently I have not set any ingress or hpa to scale the application, if needed that can be set and configured. 
To scale application, you can change the replicas that set in values.yaml
If scaling replicas are not sufficient then it can be done with applying hpa (horizontal pod autoscaler).
