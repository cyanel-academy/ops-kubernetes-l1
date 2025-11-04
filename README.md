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

- Naviguer vers https://kubernetes.io/docs/tutorials/kubernetes-basics/
- Suivez les 6 étapes en utilisant l'installation minikube

# Etape 2 - Déployer un site web

Un site web est constitué de 3 briques principales :

1. Un portail web
2. Une application backend (back office
3. Une base de données ou une API de données externes

Dans cette étape, la base de données est une API externe.

L'objectif est de mettre en place une stack web ayant l'architecture ci-desous : 

| Utilisateur | ----- HTTPS -----> | Site Web | ----- HTTPS -----> | Serveur backend |



