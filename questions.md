- How long did it take you to solve the exercise? (Please be honest, we evaluate your answer to this question based on your experience. Setting up minikube should not be counted)
	1.  To be honest the requested setup was easy. I am new to the WordPress app and its configuration with container, I went ahead and used latest image to deploy the WordPress application, then it started producing configuration errors such as "Error establishing a database connection". I did some research for this error and found that the latest WordPress image has init-script which collects the configuration details as default and preforms the application setup. which caused errors So, I selected different image which completes the requested setup for Phase one. It took around 1 and half hour to complete the setup.
	
- What would you improve if you had more time?
	1.  There is lots of scope for the improvement in this setup to achieve performance, resilience and security. I would do below configuration changes to achieve the same. 
		a. Store the password and certs in secrets and attached the secrets to the pod  
		b. Add configuration parameters such as DB name, DB Hostname and so on to ConfigMap and provide as Environment variables to application deployment.
		c. Make of Load-balancer service type to distribute the traffic.
		d. Add autoscaling feature for WordPress application tier.
		e. Deploy application on Kubernetes multi node cluster for HA.
		f. Add persistent storage for WordPress deployment to mount upload dir.
		g. Provision backups for MySQL database using scheduled dumps or volume base backup.
		h. Provision WAF solutions in front of application.
	
- Which step took most of the time? Why?
	1.  To Identify correct image of WordPress application, to achieve Phase one, because when application started with image latest tag it was giving errors "Error establishing a database connection”. It has init-script which collects the configuration details as default and preforms the application setup.
	
- How would you monitor this in production?
	1. There are various monitoring solutions available in the market. The most preferred duo for K8s cluster is Prometheus and Grafana. It gives high flexibility for what to monitor and how we want to present the data. The metrics will be CPU, Memory, Network I/O, Pod storage volume, Pod Phases (running, failed, pending). So, when new application gets deployed in namespace it can be seen in Grafana Dashboard automatically. We don’t need to worry about adding separate metrics for newly deployed application.
	2. I would also monitor the request logs for WordPress and MySQL database logs. Which are helpful to understand the current usage trends, debug errors, and root cause analysis. 
	 
	
- What would you change about this if you were going to operate it in production?
 	1. Implement a full-fledged DevSecOps delivery pipelines to perform application releases in production. The DevSecOps pipelines will consist of below stages.
		a. Maintain code base of application in standardize code revision tool.
		b. As part of build phase, continuously scan code base for smell and security vulnerabilities
		c. Maintain and standardize application docker images. 
		d. Implement continuous testing for application builds.
		e. Audit and manage production releases.
		f. Implement Alerts and notifications using quick communication channel for pipeline awareness.   
  	2. Implement monitoring solutions to collect the metrics and logs from Production.
	3. Setup alert and notifications for application failure incidence.
	4. Implement SRE (Site Reliability Engineer) practices to achieve higher up time of application.
 	5. Regularly review pre and post production activities to Identify improvements and implement the same in next release cycle. 
