
# The Legendary Git 💙


![Logo of Git](https://git-scm.com/images/logos/downloads/Git-Logo-1788C.png)

Git is a distributed version-control system for tracking changes in source code during software development, created by Linus Torvalds in 2005 for development of the Linux kernel. It is designed for coordinating work among programmers, but it can be used to track changes in any set of files. Its goals include speed, data integrity, and support for distributed, non-linear workflows[clarification needed].

If you have used the kayofeld script, you are a winner. The script installs the git and configures the necessary.

Thanks to Linus Torvalds.

# Git Cheatsheet

Liste de commandes qui peuvent servir pour utiliser les dépots Git fourni par Epitech:

## Git basic

Ajouter un fichier sous revision

```git
git add fichier
```

Enregistrer les changements

```git
git commit -m "message de commit"
```

Envoyer les changements au serveur

```git
git push
```

Récupérer les modifications depuis le serveur (à faire de préfèrence avant de push)

```git
git pull
```

Se connecter à un dépot déjà existant (remplacer depot par le nom du dépôt, login par votre login et login_prop par le login du propriétaire du dépot)

```git
git clone login@git.epitech.eu:/login_prop/depot
```

Ajouter un dépot remote à un dépot local déjà existant:

```git
git remote add origin login@git.epitech.eu:/login_prop/depot
git push origin master
```

## Gestion du dépot Epitech avec BLIH

Créer un dépot de rendu

```blih
blih repository create nom_du_depot
```

Donner les accès au dépot (remplacer login par le login de la personne pour qui vous voulez donner les droits).
Les droits d'accès existant sont: r (lecture seul), w (écriture seul) et rw (lecture et écriture).
Attention, si vous donnez uniquement w la personne ne pourra pas clone le dépot, ni récupérer les changements.

```blih
blih repository setacl nom_du_depot login rw
```

Voir les droits d'accès du dépots:

```blih
blih repository getacl test
```

## Gestion de plusieurs repos

Je possède un serveur privé sur le quel j'envois mes commits en plus du dépot d'epitech.
Voici quelques commandes pour gérer un tel cas.

Ajouter un serveur remote
```git
git remote add nom_remote user@url_remote
```

Envois d'une branch à remote
```git
git push -u nom_remote branch
```

Créer un repertoire sur remote (pour pouvoir lui envoyer ce que vous avez déjà fait)
```bash
mkdir repository && cd repository
git init --bare
```
Ajouter une branch provenant d'un remote.

```git
git fetch remote branch_remote:branch_local
```