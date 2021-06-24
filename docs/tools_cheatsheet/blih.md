The Bocal Lightweight Interface for Humans, BLIH is the EPITECH repository management tool.
A student from the class of 2021 created a WEB interface called [BLIH web](https://github.com/maximelouet/blih-web).
Throughout the school year, you're going to have to submit projects on Epitech servers.

If you have used the [kayofeld script](https://github.com/kayofeld/script-installation-ordinateur-epitech), you are a `winner`. The script installs the BLIH and configures the necessary.
Else, following these steps :

Generate a new key, that is stored as a file and will allow you to authenticate yourself on the submittal system and secure the data exchanges.

Here, you will leave all of the default values by simply pressing enter each time.
```bash
$ ssh-keygen
```

By default, the ssh key was generated in a file on your pc, in your home ~/.ssh/.
```bash
$ ls ~/.ssh/
```

You can see in this folder (~/.ssh), there are two files.

Now all you have to do is link your ssh key to blih by using this command, and enter your UNIX password (Epitech Password)

```bash
$ blih -u "surname.name@epitech.eu" sshkey upload ~/.ssh/id_rsa.pub
```

Now, BLIH is ready to be used.

- You can create a repository using:

```bash
$ blih -u "surname.name@epitech.eu" repository create repo_name
```

`repo_name: for example, CPool_Day01_2020`

- To give read permissions to `Nao Marvin`

```bash
$ blih -u "surname.name@epitech.eu" repository setacl repo_name ramassage_tek r
```

- If you work with another person in the project, you can give him person using:

```bash
$ blih -u "surname.name@epitech.eu" repository setacl repo_name hisSurname.hisName@epitech.eu rwx
```

`Note that r is for read, w for write et x for excute.`

- If you want to see who has permissions in your repo, you can type:

```bash
$ blih -u "surname.name@epitech.eu" repository getacl repo_name
```

- If you want to delete a repo,

```bash
$ blih -u "surname.name@epitech.eu" repository delete repo_name
```

- There are other commands, you can type

```bash
$ blih -h
```

You can find the official repo of blih [here](https://github.com/bocal/blih).

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

and press `Enter` 3 times.
Then, type,

```
$ ezb upload
```

The commands of ezblih are not very different from those of blih. It's just simpler. You can do the same actions as before using the commands below. ezblih will do the work for you. Use the following commands preceded by `ezblih`.

upload

create repo_name

setacl repo_name user rights

getacl repo_name

delete repo_name

If you don't want to type your email and password for each command, you can create an .env file in an ezblih folder that you also created in your home directory.

```
~/ezblih/.env
```

Then fill the `.env` file with the content :

    BLIH_EMAIL=surname.name@epitech.eu
    BLIH_PASSWORD=your_password

It is possible to fill only the email, in this case only the password will be asked.

You can find the official repo of ezblih [here](https://github.com/Rikette/ezblih).

---

A simple script can be used to retrieve your old repo:

`Using Blih`
```bash
for repo in `blih repository list`; do
    git clone $USER@git.epitech.eu:/$USER/$repo;
done
```
`Using ezblih`
```bash
for repo in `ezblih list`; do
    git clone $USER@git.epitech.eu:/$USER/$repo;
done
```

`$USER` is your epitech login

This script retrieves all the repositories present on blih in the current directory. This procedure can therefore take some time.

You can also access all your repo on this site [Blih Web](https://blih.saumon.io/)