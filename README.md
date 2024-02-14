# RsFaaS-Execution-anonyme-des-FaaS
## Objectif du projet
![image](https://github.com/Franck700/RsFaaS-Execution-anonyme-des-FaaS/assets/59613798/2e096198-9b87-4768-88d9-22e3b97fa97e)

## Choix du framework FaaS
Nous avons choisi le framework OpenFaaS pour réaliser notre projet 
## Installation d'OpenFaaS
Les étapes générales d’installation décrites dans ce document sont les suivantes :
1) Docker
2) Kind : Outil permettant d’exécuter des clusters Kubernetes locaux à l’aide de nœuds de conteneur Docker
3) Kubectl : outil en ligne de commande Kubernetes
4) Arkade : Outil pour installer facilement des applications sur un cluster Kubernetes
5) OpenFaaS
### Installation de Docker

$ sudo apt update

$ sudo apt install -y docker.io 

$ sudo systemctl enable docker --now

$ docker

### Installation d'Arcade
$ curl -sLS https://dl.get-arkade.dev | sudo sh

### Installation de Kubectl
$ arkade get kubectl

### Installation de Kind

### Installation d'OpenFaaS
$ arkade install openfaas

$ kubectl get pods -n openfaas


