# Déploiement de Jenkins sur Kubernetes

Ce guide vous montrera comment installer Jenkins sur un cluster Kubernetes en utilisant des fichiers YAML.

## Étapes de déploiement

1. **Création de l'espace de noms** : Commencez par créer un espace de noms pour Jenkins. Cela est utile pour séparer les outils DevOps des autres applications.

2. **Comptes de service et volumes** : Créez un fichier `serviceAccount.yaml` pour le compte de service admin et un `volume.yaml` pour le volume persistant. Remplacez le nom du nœud de travail par celui de votre cluster.

3. **Déploiement de Jenkins** : Utilisez `deployment.yaml` pour définir le déploiement de Jenkins. Utilisez un volume persistant local pour les données Jenkins. Pour les cas d'utilisation en production, optez pour un volume persistant spécifique au cloud.

4. **Accès au tableau de bord Jenkins** : Créez un `service.yaml` pour exposer Jenkins en tant que service de type NodePort. Cela permettra d'accéder à Jenkins via les adresses IP des nœuds sur le port 32000. Utilisez `kubectl` pour obtenir le mot de passe admin initial à partir des journaux du pod.

Assurez-vous de suivre les étapes détaillées et d'utiliser les fichiers manifestes appropriés pour une configuration réussie.


kubectl create namespace jenkins
kubectl create -f jenkins-deployment.yaml -n jenkins
kubectl get deployments -n jenkins
kubectl create -f jenkins-service.yaml -n jenkins
minikube ip
kubectl get pods -n jenkins