sudo usermod -a -G microk8s apatil
newgrp microk8s

microk8s status --wait-ready
microk8s enable dashboard dns registry istio
microk8s dashboard-proxy 

alias mkctl="microk8s kubectl" 
microk8s kubectl get all --all-namespaces
mkctl get all --all-namespaces # After Setting up the alias 

# To apply changes 
mkctl apply -f first-pod.yml 
mkctl apply -f first-pod.yml 
mkctl exec webapp -- ls
mkctl -it exec webapp sh # -it: interactive terminal

# Get the more information on the MicroK8s node 
mkctl describe node [microk8s kubectl describe node]
mkctl get nodes -o wide [microk8s kubectl get nodes -o wide]

mkctl describe pod webapp
mkctl describe svc fleetman-webapp

mkctl get po --show-labels
mkctl get po --show-labels -l release=0

microk8s kubectl delete po webapp-release-0-5 


