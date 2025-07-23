# Ansible-role-kubectl-installer

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/willbrid/ansible-role-kubectl-installer/blob/main/LICENSE) [![CI](https://github.com/willbrid/ansible-role-kubectl-installer/actions/workflows/ci.yml/badge.svg)](https://github.com/willbrid/ansible-role-kubectl-installer/actions/workflows/ci.yml)

Le rôle **ansible-role-kubectl-installer** permet d’installer **kubectl**, l’outil en ligne de commande permettant d'interagir avec un cluster Kubernetes, sur les systèmes Linux. L’installation se fait en téléchargeant le binaire officiel depuis le site de Kubernetes et en le plaçant dans un répertoire binaire système (par défaut **/usr/local/bin**).

## Exigences

- Distributions **RedHat** ou **Debian**

## Description des Variables

|Nom|Type|Description|Obligatoire|Valeur par défaut|
|---|----|-----------|-----------|-----------------|
`kubectl_version`|str|numéro de version de kubectl. Format : vx.y.z|non|`"stable"`
`should_verify_kubectl_checksum`|bool|dire s'il faut vérifier l'intégrité du fichier binaire de kubectl après téléchargement|non|`true`

## Dépendances

Aucune.

## Exemple Playbook

- Installation du rôle

```bash
mkdir -p $HOME/install-kubectl
```

```bash
vim $HOME/install-kubectl/requirements.yml
```

```yaml
- name: ansible-role-kubectl-installer
  src: git+https://github.com/willbrid/ansible-role-kubectl-installer.git
  version: v0.0.1
```

```bash
cd $HOME/install-kubectl && ansible-galaxy install --force -r requirements.yml
```

- Utilisation du rôle dans un playbook

```bash
vim $HOME/install-kubectl/playbook.yml
```

```yaml
---
- hosts: localhost
  become: true
  vars:
    kubectl_version: "stable"
    should_verify_kubectl_checksum: true

  roles:
    - ansible-role-kubectl-installer
```

```bash
cd $HOME/install-kubectl && ansible-playbook playbook.yml
```

## Licence

MIT

## Informations sur l'auteur

William Bridge NGASSAM
