## Install wordpress and mysql on minikube



-	Assuming minikube and kubectl is already installed.
		
		
		minikube Start
		
	
-	Deploy application from Phase-one folder
		
		kubectl apply -f Phase-one/wp-vanila-deployment.yaml
		

-	Get ip information of minikube
		
	
		minikube ip
		
	  
-	It will give ip address 192.168.99.X range. Put that ip address in browser alog with 32001 port to access the application
		e.g. 
		
		 http://192.168.99.111:32001


	
-	Deploy application from Phase-two folder
		
	
		kubectl apply -f Phase-two/wp-mysql-deployment.yaml
		
	
-	Try to hit same minikube ip address and port 32002 e.g.
		
		http://192.168.99.111:32002
