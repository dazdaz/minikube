## Deploying minikube on MacOSx
```
brew install kubectl
brew cask install minikube
# replace virtualbox with xhyve
brew install docker-machine-driver-xhyve

minikube start --vm-driver=xhyve --kubernetes-version="v1.8.2"

minikube start \
  --memory 8096 \
  --extra-config=controller-manager.horizontal-pod-autoscaler-upscale-delay=1m \
  --extra-config=controller-manager.horizontal-pod-autoscaler-downscale-delay=2m \
  --extra-config=controller-manager.horizontal-pod-autoscaler-sync-period=10s

minikube start --extra-config=apiserver.Authorization.Mode=RBAC

kubectl get nodes
```

```
minikube stop
minikube delete
```

## Deploying minikube on Windows
* https://storageapis.googleapis.com/kubernetes-release/relese/v1.8.2/bin/windows/amd64/kubectl.exe
* https://github.com/kubernetes/minikube/releases and download : minikube-installer.exe

```
minikube start --vm-driver=hyperv --kubernetes-version="v1.8.2"
kubectl get nodes
# launch dashboard
minikube dashboard
# view dashboard url
minikube dashboard --url
# Show IP of cluster
minikube ip
```

```
kubectl run hello-minikube --image=gcr.io/google_containers/echoserver:1.4 --port=8080
kubectl expose deployment --type=NodePort
minikube service hello-minikube --url
```

## Deploy knative
```
brew install starkandwayne/kubernetes/knctl
knctl install --node-ports --exclude-monitoring
```

## Deploy an existing public Docker image as an autoscaling stateless application to Knative, in your current Kubernetes namespace:
```
knctl namespace create -n helloworld
knctl deploy \
      --namespace helloworld \
      --service hello \
      --image gcr.io/knative-samples/helloworld-go \
      --env TARGET=Rev1
```
* https://starkandwayne.com/blog/deploying-12factor-apps-to-knative/


## Links
* https://github.com/kubernetes/minikube
