# GIT useful commands

Add alias for displaying status

```
$ git config --global alias.s status
```

Display current configuration

```
$ git config --list
```

Add user configuration

```
$ git config --global user.name "Name Surname"
$ git config --global user.email name@mail.com
```

Set pull/rebase behaviour

```
$ git config --global pull.rebase true
```

Remove remote branches from local repository, that no more exist in remote repository

```
$ git remote prune origin
```

Delete the local branch that was pruned

```
$ git branch -D name-of-the-branch-to-delete
```

Show all branches

```
$ git branch -a
```

Discover the changes between two branches

```
$ git diff --name-status branch_one..branch_two
```

Compare two branches

```
$ git diff branch_one..branch_two
```


Use another identity while using multiple GitHub accounts.
```
git config core.sshcommand "ssh -i ~/.ssh/your_private_key -o IdentitiesOnly=yes -F /dev/null"
```
