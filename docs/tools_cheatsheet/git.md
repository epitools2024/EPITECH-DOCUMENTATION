![Git img](https://git-scm.com/images/logos/downloads/Git-Logo-1788C.png)

Git is a distributed version-control system for tracking changes in source code during software development, created by Linus Torvalds in 2005 for development of the Linux kernel. It is a powerful tool designed for coordinating work among programmers, but it can be used to track changes in any set of files. Its goals include speed, data integrity, and support for distributed, non-linear workflows [clarification needed].

If you have used the [kayofeld script](https://github.com/kayofeld/script-installation-ordinateur-epitech), you are a `winner`.

After creating your repo, you will have to clone it using:

```bash
$ git clone surname.name@git.epitech.eu/surname.name@git.epitech.eu/repo_name
```

If you are not the owner of the repo, replace the second surname.name by the owner login.

Now you can create a file/folder and start working. You have to use these three commands every time you want to update your repository content remotly. 

```bash
git add <your_file> // you can use `git add .` to add all the files you modified locally
git commit -m "commit_message"
git push origin <the_remote_branch_you_want_to_push_on> // generally referred to as 'master' or 'main'
```

If you are working with someone on the project, you can retrieve the changes from the server with:

```bash
git pull origin <the_branch_on_which_the_files_have_been_pushed>
```

There are a lot of git commands to manage your code, especially when you are working on a project together. You can see a summary of the commands you can use on these sites.

- [Git CheatSheet](https://ndpsoftware.com/git-cheatsheet.html#loc=index)

- [Git CheatSheet by GITHUB](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf)