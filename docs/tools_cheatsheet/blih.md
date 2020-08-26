The Bocal Lightweight Interface for Humans, BLIH is the EPITECH repository management tool.
A student from the class of 2021 created a WEB interface called [BLIH web](https://github.com/maximelouet/blih-web).
Throughout the school year, you're going to have to submit projects on Epitech servers.

If you have used the kayofeld script, you are a winner. The script installs the BLIH and configures the necessary.
Else, following these steps :

- Generate a new key, that is stored as a file and will allow you to authenticate yourself on the submittal system and secure the data exchanges.

Here, you will leave all of the default values by simply pressing enter each time.
```
$ ssh-keygen
```

By default, the ssh key was generated in a file on your pc, in your home ~/.ssh/ .
```
$ ls ~/.ssh/
```

You can see in this folder (~/.ssh), there are two files.

Now all you have to do is link your ssh key to blih by using this command, and enter your UNIX password (Epitech Password)

```
$ blih -u "prenom.nom@epitech.eu" sshkey upload ~/.ssh/id_rsa.pub
```

Now, BLIH is ready to be used.

You can also use this script in python for a good user experience

Thanks to blih tool.

You can also use ezblih
Install ezblih with npm (install npm if you don't have it)
Configure ezblih correctly
use ezblih instead of blih. More efficient

EZ Blih
Installation de Blih via NPM sans aucune dépendance (pas de python, full JS).

Installation
Pre-requis
NodeJS - Version 8 Minimum
Je ne vais pas faire un tuto pour installer Node. Sous Windows / Mac c’est un simple installer, sous Linux utilisez le gestionnaire de paquet de votre distribution.

Installer le package en global
sudo npm i -g ezblih
Upload cle ssh
ssh-keygen
(Presser 3 fois Enter)

ezb upload
Commandes
ezb [commande]
Commandes disponnibles :

upload
list
ping
create nom_du_depot
setacl nom_du_depot user droits
getacl nom_du_depot
delete nom_du_depot
clone nom_du_depot
Configuration
Si vous êtes un gros flemmard et que vous ne souhaitez plus taper votre email et mot de passe a chaque commande, vous pouvez créer un fichier .env dans un dossier ezblih que vous aurez également créé dans votre repertoire home.

~/ezblih/.env

Remplissez ensuite le fichier .env avec comme contenu :

BLIH_EMAIL=votre.email@epitech.eu
BLIH_PASSWORD=votremdp
Il est possible de renseigner uniquement le mail, dans ce cas seulement le mot de passe vous sera demandé.

Mise à jour
sudo npm update -g ezblih

Les projets rendus à travers blih ou rendu peuvent simplement être récupéré par un étudiant.

La commande blih peut lister les dépôts avec blih repository list. Il est ensuite possible de cloner ce dépôt avec la commande git clone $USER@git.epitech.eu:/$USER/depot.

Un simple script permet de récupérer les anciens rendus :

for repo in `blih repository list`; do
    git clone $USER@git.epitech.eu:/$USER/$repo;
done
Ce script récupère tous les dépôts présents sur blih dans le répertoire courant. Cette procédure peut donc prendre un certain temps.

https://www.npmjs.com/package/blih

https://blih.saumon.io/