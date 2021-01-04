# k8s
Devops training, learning, resources, etc...

# External Test

1. [ Further Reading & References ](#refs)

<a name="refs"></a>
## Further Reading & References
- [Udemy - Learn DevOps: The Complete Kubernetes Course](https://www.udemy.com/course/learn-devops-the-complete-kubernetes-course/learn/lecture/6121104#overview)
- [Andrew Lock - Intro to Kubernetes](https://andrewlock.net/deploying-asp-net-core-applications-to-kubernetes-part-1-an-introduction-to-kubernetes/)
- [Project Tye](https://github.com/dotnet/tye/blob/master/docs/README.md)
- [Minikube](https://minikube.sigs.k8s.io/docs/handbook/controls/)






----------------


52.59.221.238

Link to the course:
	## https://www.udemy.com/course/learn-devops-the-complete-kubernetes-course/

Resources:
	## https://12factor.net/

Linux notes: 
- Service Management
	## service --status-all
	## sudo service docker start
	
- Docker 
	## docker login
	## docker build .  -t docker-demo:kubernetes // the -t is to give a <username>/<name>:<tag> to the image that we are going to build
	## docker run -p 3000:3000 -t 8c2b05ef0a18 // where 8c2b05ef0a18 is the image. Therefore we are specifying it to create and run a container based on the image 8c2b05ef0a18
	## docker tag <image-id> <username>/<repository> // the repository should be created on docker hub
	## docker push <username>/<repository>
	
- Misc
	## cp -a . ~/docker-demo //will copy recursively even hidden files from the current dir to the ~/docker-demo directory 
	## curl localhost:port
	
- DNS Troubleshooting 
	## sudo apt-get install bind9-host 
		-- host -t NS mgkmarco.tk // this is the command to check that the nameservers returned are as specified. So if using Route53 on AWS, the returned NSs should reflect that

- SSH Keygen
	## ssh-keygen -f .ssh/id_rsa 
		### In the above command... it will generate a public key id_ras.pub and the private key wil be id_rsa. So if you had to run cat id_pub it will show you the PK whereas cat id_rsa.pub will show the PBK
		
- Minikube
	## minikube start //will start the cluster 
	## minikube delete // will stop the cluster and delete anything it has created  
	## minikube dashboard // will launch a dashboard for kubernetes 
	## minikube service <name-of-the-service> --url // If the service is exposed, this will list its url 

- KOPS 
	## kops create cluster --name=kubernetes.mgkmarco.tk --state=s3://kops-state-udemy-k8s-complete --zones=eu-central-1a --node-count=2 --node-size=t2.micro --master-size=t2.micro --dns-zone=kubernetes.mgkmarco.tk		
		### To get the ZONE when using AWS, go to EC2 and navigate to the current region. From there you should get the zone details
	## kops delete cluster kubernetes.mgkmarco.tk --state=s3://kops-state-udemy-k8s-complete
	## kops validate cluster --state=s3://kops-state-udemy-k8s-complete
	
- KubeCtl
	## kubectl get node
	## kubectl get services
	## kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4
	## kubectl create -f <location-of-the-yml>  // -f flag represents to get the filename for the configuration yml
	## kubectl expose deployment hello-minikube --type=NodePort --port=8080
	## kubectl expose pod mgkmarco.nodehelloworld.example.com --type=NodePort --port=1234 --name=helloworld-service //to expose a pod 
	## kubectl get pod // Get information about all running pods
	## kubectl describe pod <pod> // Describe one pod
	## kubectl describe service <service-name> // Describe one service
	## kubectl expose pod <pod> --type=NodePort --name <name-of-the-service> // This will expose a port for the pod with a given name
	## kubectl expose pod <pod> --port=444 --name=frontend //Expose the port of a pod (creates a new service)
	## kubectl port-forward <pod> <host>:<pod-port> //Port forward the exposed pod port to your local machine
	## kubectl attach <podname> -i //Attach to the pod. Can be used to see logs etc...
	## kubectl exec <pod> -- command //Execute a command on the pod
	## kubectl logs <pod> // maybe there are some logs 
	## kubectl label pods <pod> mylabel=awesome //Add a new label to a pod
	## kubectl run -i --tty busybox --image=busybox --restart=Never -- sh //Run a shell in a pod - very useful for debugging
	## kubectl get deployments // Get information on current deployments
	## kubectl get rs // Get information about the replica sets
	## kubectl get pods --show-labels // get pods, and also show labels attached to those pods
	## kubectl rollout status deployment/helloworld-deployment // Get deployment status
	## kubectl set image deployment/helloworld-deployment k8s-demo=k8s-demo:2 // Run k8s-demo with the image label version 2
	## kubectl edit deployment/helloworld-deployment // Edit the deployment object
	## kubectl rollout status deployment/helloworld-deployment // Get the status of the rollout
	## kubectl rollout history deployment/helloworld-deployment // Get the rollout history
	## kubectl rollout undo deployment/helloworld-deployment // Rollback to previous version
	## kubectl rollout undo deployment/helloworld-deployment --to-revision=n // Rollback to any version version
	## kubectl cluster-info dump
	
	
