# ops-kubernetes-L1
Découverte de Kubernetes

# Introduction

Ce cours vise à faire découvrir l'infrastructure et l'administration de kubernetes

# Préparation 

## Installer les outils

Les outils sont :
- Un environnement Linux (Git bash, Ubuntu...)
- Docker (Système de conteneurs)
- Minikube (Cluster de développement Kubernetes)
- Kubectl (Client d'administration de Minikube)

Lien officiel vers l'installation des outils de développement : https://kubernetes.io/docs/tasks/tools/

# Etape 1 - Les tutoriels Kubernetes

## Les bases via la documentation de Kubernetes

- Naviguer vers https://kubernetes.io/docs/tutorials/kubernetes-basics/
- Suivez les 6 étapes en utilisant l'installation minikube

## Résumé 

### Concepts

- Kubernetes gère des objets dont les objectifs sont d'héberger des applications et de les maintenir opérationnelles
- Ces objets ont un type (Pod, Service, Deployment ...)
- Ces objets ont tous un ensemble de propriétés associés (Nom, label, annotations)
- Ces objets ont tous un satut au sein du cluster pour déterminer son fonctionnement
- Ces objets sont plus moins fortement couplés (selectors)

### Stack la plus basique

La base d'une stack est la suivante : 

- Un Pod contient une application (ou une partie de l'application)
- Idéalement ce Pod n'est pas créé directement mais avec à minima un Ojbet "Deployement" qui sera chargé de le faire (comme un contrat passé avec le cluster)
- Ce Pod est accessible grâche à un objet "Service". il est particulièrement important, il va permettre de créer une abstraction entre le client qui demande l'accès à la ressource, et le Pod lui même.

Plusieurs avantages : 
- Le Deployment va gérer les conditions d'opération comme :
-   Créer le(s) Pod(s)
-   Maintenir le nombre de Pod demandé
-   Avoir plusieurs Pods de la même applications sans les gérer manuellement
- Le Service va gérer le traffic vers les Pods entre les différents Pods et noeuds du réseau
-  Offrir un nom de domaine interne

### Les commandes d'administation de base

Les commandes d'administation sont casiments toutes sur le même schéma : 

kubectl [action à faire] [type d'objet à manipuler] [nom de la ressource à manipuler] [options supplémentaires]

Voici des exemples

```Shell
#Affiche tous les pods du cluster
kubectl get pod -A

#Décrit un deployement
kubectl describe deployment web-sevice -n web-namespace

#Détruire un service
kubectl delete service web-service-svc -n web-namespace
```

# Etape 2 - Déployer un site web

Un site web est constitué de 3 briques principales :

1. Un portail web
2. Une application backend (back office
3. Une base de données ou une API de données externes

Dans cette étape, la base de données est une API externe.

L'objectif est de mettre en place une stack web ayant l'architecture ci-desous : 

| Utilisateur | ----- HTTPS -----> | Site Web | ----- HTTPS -----> | Serveur backend |

# Etape 3 - Déployer des outils de supervision

L'objectif est de déployer un système de supervision basé sur plusieurs outils : 

- Grafana pour exploiter visuellement les données
- Promethus pour remonter des métriques à Grafana
- Un exporter linux pour récupérer des données sur un environnement linux
- Un exporter kubernetes pour récupérer des métriques du cluster lui-même

## From scratch (kube manifest)

[TP Monter une stack de supervision from scratch](supervision/1.supervision_manifest.md)


