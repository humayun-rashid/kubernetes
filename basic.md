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



