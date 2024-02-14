# RsFaaS-Execution-anonyme-des-FaaS
## A) Objectif du projet
![image](https://github.com/Franck700/RsFaaS-Execution-anonyme-des-FaaS/assets/59613798/2e096198-9b87-4768-88d9-22e3b97fa97e)

## B) Choix du framework FaaS
Nous avons choisi le framework OpenFaaS pour réaliser notre projet 
## C) Installation d'OpenFaaS
Les étapes générales d’installation décrites dans ce document sont les suivantes :
1) Docker
2) Kind : Outil permettant d’exécuter des clusters Kubernetes locaux à l’aide de nœuds de conteneur Docker
3) Kubectl : outil en ligne de commande Kubernetes
4) Arkade : Outil pour installer facilement des applications sur un cluster Kubernetes
5) OpenFaaS
### 1) Installation de Docker

$ sudo apt update

$ sudo apt install -y docker.io 

$ sudo systemctl enable docker --now

$ docker

### 2) Installation d'Arcade
$ curl -sLS https://dl.get-arkade.dev | sudo sh

### 3) Installation de Kubectl
$ arkade get kubectl

### 4) Installation de Kind
$ wget https://dl.google.com/go/go1.16.3.linux-amd64.tar.gz

$ nano kind-with-registry.sh

$ chmod +x kind-with-registry.sh

$ ./kind-with-registry.sh

$ kubectl config current-context

$ kubectl config use kind-kind

$ kubectl cluster-info


### 5) Installation d'OpenFaaS
$ arkade install openfaas

$ kubectl get pods -n openfaas

## D) Ajout d'une fonction dans OpenFaaS

Nous avons implémenté une fonction dictionnaire avec python. Pour créer cette fonction, nous avons suivi les étapes suivantes : 

1) $ faas-cli new pydict --lang python3-flask-debian
2) $ kubectl get service -n openfaas
3) $ kubectl port-forward -n openfaas svc/gateway 8080:8080 &
4) $ faas-cli build -f pydict.yml
5) $ faas-cli push -f pydict.yml
6) $ PASSWORD=$(kubectl get secret -n openfaas basic-auth -o jsonpath="{.data.basic-auth-password}" | base64 --decode; echo)
7) $ env | grep PASSWORD
8) $ echo -n $PASSWORD
9) $ faas-cli deploy -f pydict.yml -g http://127.0.0.1:8080
10) $ kubectl get pods -n openfaas-fn

### 1) Test de la fonction
1) curl -X POST http://localhost:8080/function/pydict -d '{"word":"night"}' : cette commande va rechercher le mot "night" dans le dictionnaire
2) Nous pouvons également ouvrir le lien http://127.0.0.1:8080 pour avoir rechercher les mots dans le site web avec une interface graphique. Il faut entrer les credentials de connexion pour se connecter au site 

## E) Vidéo décrivant la solution

Partie 1 : https://drive.google.com/file/d/1l02jqhVYb4Pfjl0Dxph2wzQlAPh1oqrF/view?usp=drive_link

Partie 2 : https://drive.google.com/file/d/1g2xzJsOLo2V3aMFFvKn9nRXf_G5xON8P/view?usp=drive_link
