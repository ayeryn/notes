# Useful Github Commands

## Delete local branch

```console
$ git branch -d <branch>
```

## Git Alias

### Set Alias

```console
$ git config --global alias.co checkout
```

### List Alias

```console
$ git config -l | grep alias
```

### Stash and Pop Changes

1. Save changes to branch A
2. Run `git stash`
3. Check out branch B
4. Fix the bug in branch B
5. Commit and (optionally) push to remote
6. Check out branch A
7. Run `git stash pop` to get your stashed changes back
