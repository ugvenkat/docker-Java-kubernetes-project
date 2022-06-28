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
 Download  "Generic Java Package (.war) from https://www.jenkins.io/download/
 java -jar jenkins.war
 This will provide the initial password.
 navigate to localhost:8080 
 Enter the initial password and continue. 
 Customize Jenkins
    Click "Install Suggested plugins"   ("This will take some time")

 Create First Admin User ("Fill all the details")
   Proceed to all the prompts.
 Finally you will see Jenkins running.




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