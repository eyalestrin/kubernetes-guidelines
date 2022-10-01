# Install Kubectl
* Install and Set Up kubectl on Windows:  
  https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/
* Install and Set Up kubectl on Linux:  
  https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/
* Install and Set Up kubectl on macOS:  
  https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/

# Install Amazon Elastic Kubernetes Service (EKS) cluster:
1. Installing eksctl:  
  https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html
2. Create EKS cluster using eksctl:  
  https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html#create-cluster-gs-eksctl
3. Check EKS cluster status:  
  **<code>aws eks --region us-east-1 describe-cluster --name my-eks-cluster --query cluster.status</code>**  
4. Add a context for EKS cluster in Kube config of the machine:  
  **<code>aws eks --region us-east-1 update-kubeconfig --name my-eks-cluster</code>**  

# Install Azure Kubernetes Service (AKS) cluster:
1. Install Azure CLI:  
  https://learn.microsoft.com/en-us/cli/azure/install-azure-cli
2. Deploy an Azure Kubernetes Service cluster using the Azure CLI:  
  https://learn.microsoft.com/en-us/azure/aks/learn/quick-kubernetes-deploy-cli

# Install Google Kubernetes Engine (GKE) cluster:
1. Download and install the gcloud CLI:  
  https://cloud.google.com/sdk/gcloud#download_and_install_the
2. Create a GKE cluster:  
  https://cloud.google.com/kubernetes-engine/docs/deploy-app-cluster#create_cluster
3. Authenticate to Google Container Registry:  
  **<code>gcloud auth configure-docker</code>**  
4. Get authentication credentials for the cluster (in Google Cloud):  
  **<code>gcloud container clusters get-credentials [CLUSTER-NAME]</code>**  

# Common Kubectl commands:
* Print the client and server version of Kubectl:  
  **<code>kubectl version</code>**  
* Get a list of nodes:  
  **<code>kubectl get nodes</code>**  
* Get a list of pods:  
  **<code>kubectl get pods</code>**  
* List all pods in ps output format with more information:  
  **<code>kubectl get pods -o wide</code>**  
* Get a list of deployment:  
  **<code>kubectl get deployment</code>**  
* Describe a node:  
  **<code>kubectl describe nodes kubernetes-node-emt8.c.myproject.internal</code>**  
* Describe a pod:  
  **<code>kubectl describe pods/nginx</code>**  
* Describe all pods:  
  **<code>kubectl describe pods</code>**  
* Return snapshot logs from pod nginx with only one container:  
  **<code>kubectl logs nginx</code>**  
* Get output from running the 'date' command from pod mypod, using the first container by default:  
  **<code>kubectl exec mypod -- date</code>**  
* Run shell command inside a pod:  
  **<code>kubectl exec -it [POD_NAME] sh</code>**  
* Show environment variables insie a pod:  
  **<code>kubectl exec -it nginx -- env</code>**  
* Start a nginx pod:  
  **<code>kubectl run nginx --image=nginx</code>**  
* Get a list of namespaces:  
  **<code>kubectl get namespace</code>**  
* Get all details about a namespace:  
  **<code>kubectl describe ns [namespace]</code>**  
* Create a new namespace:  
  **<code>kubectl create namespace [namespace]</code>**  
* Edit definition of specific name space:  
  **<code>kubectl edit ns [name space]</code>**  
* Get pod information from a specific namespace:  
  **<code>kubectl get pods -n [namespace]</code>**  
* Delete a specific namespace:  
  **<code>kubctl delete ns [namespace]</code>**  
* Set a context entry in kubeconfig:  
  **<code>kubectl config set-context --current --namespace=[NAMESPACE NAME]</code>**  
* Show merged kubeconfig settings:  
  **<code>kubectl config view --minify | grep namespace</code>**  
* Print all objects that can exist inside namespace:  
  **<code>kubectl api-resources --namespaced=true</code>**  
* Print all object that cannot exist inside namespace:  
  **<code>kubectl api-resources --namespaced=false</code>**  
* Show resource quota:  
  **<code>kubectl api-resources --namespaced=true | grep resourcequotas</code>**  
* Check the rollout status of a daemonset:  
  **<code>kubectl rollout status daemonset/foo</code>**  
* View the rollout history of a deployment:  
  **<code>kubectl rollout history deployment/abc</code>**  
* Roll back to the previous deployment:  
  **<code>kubectl rollout undo deployment/abc</code>**  
* Roll back to daemonset revision 3:  
  **<code>kubectl rollout undo daemonset/abc --to-revision=3</code>**  
* Update image in existing deployment:  
  **<code>kubectl set image [image-name] --namespace [namespace] [container-name]=[new-image-name]</code>**  
* Update pod 'foo' with the annotation 'description' and the value 'my frontend running nginx', overwriting any existing value:  
  **<code>kubectl annotate --overwrite pods foo description='my frontend running nginx'</code>**  
* Show information about replica-sets in a deployment:  
  **<code>kubectl get replicasets</code>**  
  **<code>kubectl get rs -n [namespace]</code>**  
* Listen on ports 5000 and 6000 locally, forwarding data to/from ports 5000 and 6000 in the pod:  
  **<code>kubectl port-forward pod/mypod 5000 6000</code>**  
  **<code>kubectl port-forward <pod name> [Local_Port:Remote_Port]</code>**  
* Attach a running process inside existing container:  
  **<code>kubectl attach <pod name> -c <container></code>**  
* Delete a pod:  
  **<code>kubectl delete pod foo</code>**  
  **<code>kubectl delete pods [pod_name]</code>**  
* Delete all pods:  
  **<code>kubectl delete pods --all</code>**  
* Create a deployment named my-dep that runs the busybox image:  
  **<code>kubectl create deployment my-dep --image=busybox</code>**  
  **<code>kubectl create deployment mypod3 --image yanivomc/spring-music:latest --port=8080</code>**  
  **<code>kubectl create deployment mypod3 --image yanivomc/spring-music:latest --port=8080 --replicas 3</code>**  
* Create a deployment with a command:  
  **<code>kubectl create deployment my-dep --image=busybox -- date</code>**  
* Create YAML file:  
  **<code>kubectl create deployment nginx --image nginx:latest --dry-run=client -o yaml</code>**  
* Delete a deployment:  
  **<code>kubectl delete deployment webapp</code>**  
* List all Services:  
  **<code>kubectl get services</code>**  
* Show the particular Service:  
  **<code>kubectl get service <NAME></code>**  
* Show information about all services:  
  **<code>kubectl get svc -A</code>**  
* Get the Service details:  
  **<code>kubectl describe services</code>**  
  **<code>kubectl describe service <NAME></code>**  
* Create a new service:  
  **<code>kubectl create service clusterip [deployment_name] --tcp=8888:8080</code>**  
* Edit the service named 'registry':  
  **<code>kubectl edit svc/registry</code>**  
* Delete a service:  
  **<code>kubectl delete service/[service name]</code>**  
* Create a service for an nginx deployment, which serves on port 80 and connects to the containers on port 8000:  
  **<code>kubectl expose deployment nginx --port=80 --target-port=8000</code>**  
  **<code>kubectl expose deployment/mydeployment4 --type=LoadBalancer --port=80 --target-port=8080 --name=myservicename4</code>**  
* Create a new deployment:  
  **<code>kubectl create deployment mydeployment4 --image yanivomc/spring-music:latest --port=8080 --replicas 3</code>**  
  **<code>kubectl create deployment [deployment-name] --image [image-name] --namespace=[namespace] --replicas 1</code>**  
* Scale an existing deployment:  
  **<code>kubectl scale deployment/[name] --replicas=[num]</code>**  
* Configure autoscale settings:  
  **<code<kubectl autoscale deployment webapp --cpu-percent=85 --min=10 --max=20</code>**  
* Get information about HorizontalPodAutoscaler:  
  **<code>kubectl get hpa</code>**  
* Delete deployment HorizontalPodAutoscaler:  
  **<code>kubectl delete hpa webapp</code>**  
* Update pod 'foo' with the label 'unhealthy' and the value 'true':  
  **<code>kubectl label pods foo unhealthy=true</code>**  
* Apply configuration from YAML file:  
  **<code>kubectl apply -f [filename].yml</code>**  
* Delete configuration from YAML file:  
  **<code>kubectl delete -f [filename].yaml</code>**  
* List the nodes in your cluster:  
  **<code>kubectl get nodes --show-labels</code>**  
* List all nodes (update in real-time):  
  **<code>kubectl get nodes --watch</code>**  
* Create cronjob:  
  **<code>kubectl create cronjob NAME --image=image --schedule='0/5 * * * ?' -- [COMMAND] [args...]</code>**  
* Delete cronjob:  
  **<code>kubectl delete cronjob NAME</code>**  
* View the state of the Ingress:  
  **<code>kubectl get ingress</code>**  
* Create a new config map named my-config based on folder bar:  
  **<code>kubectl create configmap my-config --from-file=path/to/bar</code>**  
* Create configmap from a YAML file:  
  **<code>kubectl create -f configmaps-keyvalcfgmap.yaml</code>**  
* Get information about a configmap:  
  **<code>kubectl describe configmaps</code>**  
* Delete a configmap:  
  **<code>kubectl delete configmap [configmap_name]>/code>**  
  
