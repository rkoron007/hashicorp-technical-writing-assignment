# What is the difference between `git` push, pull, and fetch?

The below commands are a fundamental part of any developer's Git workflow:

- `git push` - The `git push` command _pushes_ a local branch's content to a remote repository.
- `git fetch` - The `git fetch` command _fetches_ content from a branch in a remote repository.
- `git pull` - The `git pull` command fetches content from a branch in a remote repository _and merges_ that content into your local branch.

You can use `git push` to share your local content (i.e., files, commits, and refs) with a remote repository:

```shell
git push <LOCAL_BRANCH> <ORIGIN>
```

> In Git, "origin" is a shorthand name for your project's associated remote repository.

When you run `git push`, Git first checks whether the remote repository has an associated branch for the local branch you are attempting to push:

- If there _is_ an associated remote branch, Git pushes changes from your local branch to that remote branch.
- If there _is not_ an associated remote branch, Git pushes your local branch up to the remote repository, adding a new remote branch.

The `git push` command can fail if your local and associated remote branches have diverged. This usually happens if your remote branch has commits that aren't on your local branch. You can fix this by synchronizing your local branch with its associated remote branch using `git pull` or `git fetch` and `git merge`.

You can use `git fetch` to download the content (i.e., files, commits, and refs) from a remote branch _without_ affecting your local work:

```shell
git fetch <REMOTE_BRANCH> <ORIGIN>
```

When you run `git fetch`, Git first checks whether your remote repository has the specified branch. If it does, Git downloads any changes from that branch to a separate local tracking branch. This tracking branch follows the naming convention `<ORIGIN>/<REMOTE_BRANCH>` (e.g., `origin/main` is your "main" branch's tracking branch). The `git fetch` command fails if it can't find the specified branch in the remote repository.

It does not change your local branch. To do that, you'll need to do `git merge origin/master` (for the "master" branch) to merge those changes into your branch - probably also called "master".

`git pull` simply does a `git fetch` followed immediately by `git merge`. This is often what we desire to do, but some people prefer to use git fetch followed by git merge to make sure they understand the changes they are merging into their branch before the merge happens.
