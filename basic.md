Basic elements of kubernetes that's are required to get started.
1. Pod 
2. Deployment
3. Service
4. Namespace

When minikube will  started, first check all the namespaces -
```
minikube get namespace
```
There should be a default namespace that is 'default'. You can not delete this one. All your deployment will be in defualt if you have not specified new namespace.

First, Create a namespace named "development"

kubectl create namespace development

So, you have created a namespace using cli. Now, let's do it by yaml. Generate the yaml file by:

kubectl create namespace development --dry-run -o yaml (It will show the yaml output. You can copy and create a file namespace.yaml)
kubectl create namespace k8s --dry-run -o yaml > namespace.yaml ( It will create a namespace.yaml in directory).

Delete the previously created namespace.
kubectl delete namespace development
create a new namespace using yaml.

kubectl create -f namespace.yaml ( If you are creating for first time)
kubectl apply -f namespace.yaml  ( If you want to update with a change in yaml)

Now, a 
great. Let's create a pod of Nginx. We need to create a .yaml file to do that. 


# Create Namespace
--dry-run =
-o yaml =
-o yaml > file-name = 

### Format:
kubectl create namespace/ns name

### Example: 
kubectl create namespace k8s

### Generate Yaml: 
kubectl create namespace k8s --dry-run -o yaml

Save to yaml file:
kubectl create namespace k8s --dry-run -o yaml -o yaml > namespace.yaml

It should create a namespace.yaml file.
Apply through kubectl. 

kubectl create -f namespace.yaml 
kubectl apply -f namespace.yaml

# Pod and Deployment with image nginx called nginx on same namespace

kubectl run name --image=image-name --restart=Always/ -n namespace --port=port number

--restart = Never > It will create Pod 
-- restart = Always > It will create deployment

Create pod in namespace 'k8s' 
kubectl run nginx --image=nginx --restart=Never --port=8080 -n k8s

Generate yaml 
kubectl run nginx --image=nginx --restart=Never --port=8080 -o yaml

kubectl run nginx --image=nginx --restart=Never --port=8080 -o yaml > pod.yaml

kubect apply -f pod.yaml 

Create deployment in namespace 'k8s' 
kubectl run nginx --image=nginx --restart=Always --port=8080 -n k8s

Generate yaml 
kubectl run nginx --image=nginx --restart=Always --port=8080 -o yaml

kubectl run nginx --image=nginx --restart=Always --port=8080 -o yaml > deployment.yaml

kubect apply -f deployment.yaml 

Alternatively, you can run in one line

kubectl run nginx --image=nginx --restart=Never --dry-run -o yaml | kubectl create -n mynamespace -f -



