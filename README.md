# K8sWebAppCluster
Create a K8s multicontainer pod cluster using YAML files for Multi tier web application deployment on your machine

STEPS TO FOLLOW:


***************************************************************************************************************************************************************
Either you can use single file `createCluster.yml` and you can directly run the command: `kubectl create -f createCluster.yml` and cluster will be created along with the secret file, and ports will be exposed too Or you can follow below steps to do using three different yaml files.
***************************************************************************************************************************************************************


1. Download all the three yaml files.<br>
2. In createDatabase file, if you want you can change the MYSQL_USER/ MYSQL_PASS. or you can adjust the number of replicas according to your requirement.(base: 1)<br>
3. In secret file, you can change the pass variable value, as this is the only password that we are using for accessing the mysql server. Make sure the password is base64 encoded.<br>
***** If you don't want to make any single change, just go on ***** the base64 encoded password in secret file is 'toor'<br>
4. You can use Serv file for exposing or you can expose your deployment manually too.<br>
5. Use command `kubectl create -f secret.yml` first to create the secret file protecting the password first.<br>
6. Use command `kubectl create -f createDatabase.yml` to create a deployment named webapplication.<br>
***** IF YOU ARE EXPOSING MANUALLY THEN YOU HAVE TO CHECK FOR THE URL WITH COMMAND: `minikube service list` and check the url with port named webapplication *****<br>
7. Use command `kubectl create -f serv.yml` to start a service that will expose your wordpress pod port 80, but you can access it via port 30400.<br>
8. Visit the URL and then install the wordpress, database name: mywpdb, user: root, password: toor, host: "check for the ip that is running mysql with command: `kubectl describe pods` and put into host section.<br>
9. Proceed to install by creating account and then login and write stuffs.<br>
Congratulations! you have successfully deployed a multitier web application on K8s cluster on your machine.

