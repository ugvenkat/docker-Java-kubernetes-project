# docker-Java-kubernetes-project
Deploying Java Applications with Docker and Kubernetes

Credit: https://github.com/danielbryantuk/oreilly-docker-java-shopping/
########################################################################


Step 1: Install Java JDK 1.8 
	https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html
 	Path = C:\Program Files\Java\jdk1.8.0_202\bin
	JAVA_HOME to C:\Program Files\Java\jdk1.8.0_202
Step 2:Install Maven 
	 https://maven.apache.org/download.cgi
	 Download and extract the zip file into C:\xTool\apache-maven-3.8.6
	 Using Environment Varialbes Setup 
	   MAVEN_HOME to C:\xTool\apache-maven-3.8.6 
	   M2_HOME to C:\xTool\apache-maven-3.8.6 
	   Path = C:\xTool\apache-maven-3.8.6\bin
Step 3: Install MiniKube
	https://minikube.sigs.k8s.io/docs/start/
	minikube start
	kubectl cluster-info

Step 3.1: Install kubectl     

Install Jenkins
 Download  jenkins.msi from https://www.jenkins.io/download/
 Run service as local user:
    Create local useraccount admin and grant logon access

--To get Logon Access. 
  Logon to the computer with administrative privileges.
  Open the ‘Administrative Tools’ and open the ‘Local Security Policy’
  Expand ‘Local Policy’ and click on ‘User Rights Assignment’
  In the right pane, right-click ‘Log on as a service’ and select properties.
  Click on the ‘Add User or Group…’ button to add the new user.
  In the ‘Select Users or Groups’ dialogue, find the user you wish to enter and click ‘OK’
  Click ‘OK’ in the ‘Log on as a service Properties’ to save changes.
 
 Account: admin
 Password: passabcbcbc
 During installaion change the port to 9090

 Get the password from the location 
 C:\Users\admin\AppData\Local\Jenkins\.jenkins\secrets\initialAdminPassword
 and enter the Administrator password:

 
 Click "Install Suggested plugins"   ("This will take some time")

 Create First Admin User ("Fill all the details")
   Proceed to all the prompts.
  Click "Start using Jenkins"





step 4: Install VisualStudio Code.
step 5: Clone
    git clone https://github.com/ugvenkat/docker-Java-kubernetes-project
    cd docker-Java-kubernetes-project
    code .
     -- Check the Dockerfile / pom.xml 
step 6:
     cd docker-Java-kubernetes-project\shopfront
     mvn clean install
     docker build -t ugvenkat/shopfront:latest .

     cd docker-Java-kubernetes-project\productcatalogue
     mvn clean install
     docker build -t ugvenkat/productcatalogue:latest .

     cd docker-Java-kubernetes-project\stockmanager
     mvn clean install
     docker build -t ugvenkat/stockmanager:latest .

step 7:
     docker images
     docker login	
     docker push ugvenkat/shopfront
     docker push ugvenkat/productcatalogue
     docker push ugvenkat/stockmanager

step 8:
     kubectl get pods
     kubectl get deployments
     kubectl get svc

step 9:
    cd docker-Java-kubernetes-project\kubernetes
    kubectl apply -f productcatalogue-service.yaml  
    kubectl apply -f shopfront-service.yaml  
    kubectl apply -f stockmanager-service.yaml  

step 10:
   minikube service shopfront
   minikube service productcatalogue
   minikube service stockmanager