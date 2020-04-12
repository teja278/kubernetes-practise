Hello!!

Hope you are doing great today. 
Here are the scripts for Task2 and Task3 and how to run them.

Task 2 - Create a nagios check that will detect if there are kafka topics that are not replicated on every kafka node. 
Script name - check_replication
- How to run : needs two parameters to provide the kafka broker hostnames and the path to bin kafka-bin
`./check_replication "--zookeeper localhost:2181" /usr/lib/kafka/bin`

Task 3 - Run the following command in the k8s folder
`kubectl apply -f .`
 1.  Set up (in kubernetes/minikube) 2 pods with a java example app:https://github.com/TechPrimers/docker-mysql-spring-boot-example
 - Built image for the source code of the example and pushed to the repo teja278/users-mysql 
 - Created a deployment config named users-api to deploy the image.
 
 2.  Load balance the traffic to the backends
 - Created a loadbalancer type service for the users-api service
 
 3. Create policy to auto-heal or recreate the pod if it goes down or is unresponsive.
 - Added a liveness and readiness probe to ensure the health of the containers. used the http endpoint /all/ , ideally it can be an endpoint like /health for springboot applications
  
 4. Add a mysql.
 - Added a mysql db. 
 
 5. Can you do a HA of a database? Any way to keep the data persistent when pods are recreated?
 - added a persistent volume to ensure no data loss on restart of pods. 
 HA of the database can be ensured by setting up a cluster for my-sql db with master and replica slaves.And using persistent volumes is a prerequisite for database maintenance activities. 
 VolumeSnapshot can be executed for backup and restore actions. 
 
 7. Split your deployment into prd/qa/dev environment.
- best practice would be to externalise the application.properties using config-maps and environment variables
- split the deployments by using a different namespace for each environment.