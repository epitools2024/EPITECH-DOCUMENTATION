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
$ blih -u "surname.name@epitech.eu" sshkey upload ~/.ssh/id_rsa.pub
```

Now, BLIH is ready to be used.

You can create a repository using:

```
$ blih -u "surname.name@epitech.eu" repository create repo_name
```

To give read permissions to Nao Marvin

```
$ blih -u "surname.name@epitech.eu" repository setacl repo_name ramassage_tek r
```

If you work with another person in the project, you can give him person using:

```
$ blih -u "surname.name@epitech.eu" repository setacl repo_name hisSurname.hisName@epitech.eu rwx
```

Note that r is for read, w for write et x for excute.

If you want to see who has permissions in your repo, you can type:

```
$ blih -u "surname.name@epitech.eu" repository getacl repo_name
```

If you want to delete a repo,

```
$ blih -u "surname.name@epitech.eu" repository delete repo_name
```
There are other commands, you can type

```
$ blih -h
```

---

You can also use ezblih

For that, you need node and npm. You can install it here depending on your os. [Node Installer](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions-enterprise-linux-fedora-and-snap-packages)

To install ezblih,

```
$ sudo npm i -g ezblih
```

Upload your ssh-keygen with

```
$ ssh-keygen
```

and press Enter 3 times.
Then, type,

```
$ ezb upload
```

The command that you can use with ezb are not different with the blih command. It's just more simple

Vous pouvez faire les memes actions que précédemment en utilisant les commandes ci-dessous. ezblih fera le travail pour vous.

upload

list

ping

create repo_name

setacl repo_name user droits

getacl repo_name

delete repo_name

Si vous êtes un gros flemmard et que vous ne souhaitez plus taper votre email et mot de passe a chaque commande, vous pouvez créer un fichier .env dans un dossier ezblih que vous aurez également créé dans votre repertoire home.

~/ezblih/.env

Remplissez ensuite le fichier .env avec comme contenu :

    BLIH_EMAIL=votre.email@epitech.eu
    BLIH_PASSWORD=votremdp

Il est possible de renseigner uniquement le mail, dans ce cas seulement le mot de passe vous sera demandé.

---

Un simple script permet de récupérer les anciens rendus :

```bash
for repo in `blih repository list`; do
    git clone $USER@git.epitech.eu:/$USER/$repo;
done
```

Ce script récupère tous les dépôts présents sur blih dans le répertoire courant. Cette procédure peut donc prendre un certain temps.

Vous pouvez également accéder à tous vos repos sur ce site [Blih Web](https://blih.saumon.io/)