### Debugging

#### In general 

* kubectl get pods
* kubectl get namespace
* kubectl get pods --all-namespaces
* kubectl get pods --show-labels
* kubectl describe pod nginx -n nginx-ns
(e.g. image tag wrong)
* kubectl edit pod nginx -n nginx-ns

#### Safely delete and re-create

* kubectl get pod nginx -n nginx-ns -o yaml --export > nginx-pod.yml
* kubectl delete pod nginx -n nginx-ns
* kubectl apply -f nginx-pod.yml -n nginx-ns

### Label selectors
* kubectl get pods -l app=my-app
* kubectl get pods -l environment=production
* kubectl get pods -l environment=development
* kubectl get pods -l environment!=production
* kubectl get pods -l 'environment in (development,production)'
* kubectl get pods -l app=my-app,environment=production

### Deployments
* kubectl get deployments
* kubectl get deployment _{deployment name}_
* kubectl describe deployment _{deployment name}_
* kubectl edit deployment _{deployment name}_
* kubectl delete deployment _{deployment name}_

#### Rolling updates
* kubectl set image deployment/rolling-deployment nginx=nginx:1.7.9 --record
* kubectl rollout history deployment/rolling-deployment
* kubectl rollout history deployment/rolling-deployment --revision=2
* kubectl rollout undo deployment/rolling-deployment
* kubectl rollout undo deployment/rolling-deployment --to-revision=1