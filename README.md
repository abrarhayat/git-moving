# Migrating Your Git Repository to a New Remote

## Are you looking to switch your Git repository to a new remote?

### Follow these simple steps to migrate your repository

Make sure you have all the remote branches available locally

```bash
git fetch --all
```

Now create local branches corresponding to remote branches

```bash
for branch in $(git branch -r | grep -v '\->'); do
    git branch --track ${branch#origin/} $branch
done
```

Rename current origin to something different, so if you are currently on bitbucket, you can name your remote to `bitbucket`:

``` bash
git remote rename origin bitbucket
```

Now add new origin remote:

```bash
git remote add origin your_new_remote_url.git
```

Push your local main branch to your new remote origin:

```bash
git push origin main
```

Optional: Push all your local branches to new origin:

```bash
git push --all origin
```

Congratulations! You've successfully migrated your repository to the new remote!
