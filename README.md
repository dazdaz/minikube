## Deploying minikube on MacOSx
```
brew install kubectl
brew cask install minikube
# replace virtualbox with xhyve
brew install docker-machine-driver-xhyve
minikube start --vm-driver=xhyve --kubernetes-version="v1.8.2"
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
minikube dashboard
```

## Links
* https://github.com/kubernetes/minikube
