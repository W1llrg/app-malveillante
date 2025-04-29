# Guide

## Installation

### Forker le repo Github

Pour cloner l'original si besoin:
```bash
git clone https://github.com/WallaceTheGreat/app-malveillante.git
```
### Sur le fork

#### Changer l'IP du serveur host

Changer l'IP du serveur host dans le fichier `inventory/hosts.ini`
```bash
ansible_host=<ip_server>
```

#### Créer un secret Github

le nommer `SSH_PRIVATE_KEY`. Sa valeur doit être la clé privée sur la machine locale.

### Déployer

Exécuter la Pipeline Github et accéder à l'application via l'IP du serveur.

### Sur la machine distance / serveur

Installer kubectl si ce n'est pas fait en suivant le tutoriel de Kubernetes:
https://kubernetes.io/releases/download/

## Informations

- Il n'y a pas de BDD dans cette version (pas de couchbase)
- Il y a une configuration Traefik mais elle n'a pas été migré sur le Kubernetes
- J'ai pas remplacé le server_ip partout donc ça ne va pas déployer malheureusement

## Architecture

- Back: API express
- Front: application vuejs