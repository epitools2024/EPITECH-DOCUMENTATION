
# EPITECH-CHEAT_SHEET by [Blacky_yg](https://github.com/blacky-yg), [NemesisX1](https://github.com/NemesisX1) and [Prince](https://github.com/CMasterp)

**EPITECH PROGRAMMERS TOOLS**

Youtube account [epitools]() and epitools website [epitools.bj]()

---
# 2. BLIH

The Bocal Lightweight Interface for Humans, BLIH is the EPITECH repository management tool.
A student from the class of 2021 created a WEB interface called [BLIH web](blih.salmon.io).
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

---

*NB: Use CTRL + F or Command + F to quickly look for keywords.*

---
[<-- Previous](https://github.com/epitools2024/EPITECH-CHEAT_SHEET/tree/master/II/Epitech_^_^_DUMP)                                                                            [Next -->](https://github.com/epitools2024/EPITECH-CHEAT_SHEET/tree/master/II/Git)