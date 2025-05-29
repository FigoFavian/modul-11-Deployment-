### 1. Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?

![alt text](image.png)

The image above shows the before and after (before at the top, the after is below) and yes, the Service is successfully routing external traffic to the Pod. This is due to he increasing tnumber of logs every time the app gets accessed because each HTTP request to the service is logged by the application.  

### 2. Notice that there are two versions of kubectl get invocation during this tutorial section. The first does not have any option, while the latter has -n option with value set to kube-system. What is the purpose of the -n option and why did the output not list the pods/services that you

![alt text](image-1.png)

"-n" is used to specify which Kubernetes namespace to query or operate on. Without it, hello-node deployment and service is shown because it is showed resources in the default namespace, which included our hello-node deployment and service. 

The output of kubectl get pods,services -n kube-system didn't list the pods/services we explicitly created because those were created in the default namespace, while the -n kube-system command only shows resources in the kube-system namespace. Kubernetes uses namespaces to logically separate and organize resources which provides isolation between different applications or environments.

But if i ran kubectl get services and kubectl get pods then it showed resources in the default namespace, which included our hello-node deployment and service.