## Minikube and Helm
This is a practice for minikube configuration. First using manifests for both components (backend and mongo database) then using Helm chart for variabilisation.  
### Minikube and manifests only
For the first practice, we have two manifests: mongo.yaml and backend.yaml, they both have the deployment and service defnition.  
In order to be able to deploy them, first start by [installing minikube](https://kubernetes.io/fr/docs/tasks/tools/install-minikube/) 
When installed, and started, we should make sure that **kubectl** is installed too, before applying the following commands:  
<p align="center"> <pre><code>
kubectl apply -f your-path-here/mongo.yaml
</code></pre></p>
We create and execute the mongo container first, and wait for it to be running before we create and execute the backend container with this command :   

<p align="center"> <pre><code>
kubectl apply -f your-path-here/backend.yaml
</code></pre></p>  

In order to see the pods and their state you can use the command :  
<p align="center"> <pre><code>
kubectl get pods
</code></pre></p>   

In order to see the logs of a pod you can use the command :  
<p align="center"> <pre><code>
kubectl logs name-of-your-pod
</code></pre></p>  


### Helm instead of manifests  
Instead of deploying each container manually, we can you the **Helm Chart** to deploy them in one time.  
We also use the **init-container** from minikube to make the backend container wait for the mongo container to be running before it starts too.  
In order to execute the application you should first [Install Helm](https://helm.sh/docs/intro/install/).  
After having minikube running, apply the command:   
<p align="center"> <pre><code>
helm install app-name path-to-helm-chart-directory
</code></pre></p>  
You can choose what you want for your application name. 

