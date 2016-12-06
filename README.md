# Building useful history

## It starts with concepts

The closer you adhere to these guidelines, the more useful your history will be:

- All commits should be **atomic**
- Smaller commits are **always** better commits
- A useful message *must* describe **why** the change was made
- A useful commit message *may* also summarize the change itself (though this is usually redundant. We'll see why later.)

## When your changes are neither small or atomic, but you still want your commits to be

### Useful commands

- `git add -p $FILE_PATH`

### Configure the lab branch

```
git checkout -b git-add-p origin/git-add-p
git apply changes.patch
```

## When you forgot to add a file to your last commit

Also when:

- You didn't make an atomic commit and you'd like to fix that

### Useful commands

- `git commit --amend` **!!!!!**

### Configure the lab branch

```
git checkout -b git-commit-amend origin/git-commit-amend
git apply changes.patch
```

## When your changes aren't ready to commit, but someone else's need to be merged in

Also when:

- You want to checkout another branch, but you aren't ready to commit your changes (and don't want to lose them!)

### Useful commands

- `git stash`
- `git stash pop`

### Configure the lab branch

```
git checkout -b good-to-merge origin/good-to-merge
git checkout -b git-stash origin/git-stash
git apply changes.patch
```

## Merge conflicts: Facing the inevitable

Also when:
- Conflicts can happen using `git rebase`
- Conflicts can happen using `git stash pop`

### Configure the lab branch

```
git checkout -b git-conflicts origin/conflict-path-a
git merge origin/conflict-path-b
```
# Making use of history

## The lab branch

```
git checkout -b git-history origin/git-history
```

## When you just want to see previous commit messages

### Useful commands

- `git log`
- `git log -$NUM`
- `git log --pretty=oneline`

## When you want to look at both the commit message and the changes it introduced

### Useful commands

- `git show $COMMIT`
- `git log -p`

## When you only want to look at commits in a certain date range

### Useful commands

- `git log --after=$DATE`
- `git log --before=$DATE`

## When you want to find commits based on the contents of the commit message

### Useful commands

- `git log --grep=$SEARCH_PATTERN`

## When you want to find the commit that changed a particular line of a particular file

### Useful commands

- `git blame $FILE_PATH`

## When you want to view the full contents of a historical file

### Useful commands

- `git show $COMMIT:$FILE_PATH`

## When you want to search the contents of historical files

### Useful commands

- `git grep $SEARCH_PATTERN $COMMIT`
- `git grep $SEARCH_PATTERN $(git rev-list --all)`
- `git grep $SEARCH_PATTERN $COMMIT_1 $COMMIT_2 $FILE_PATH_1 $FILE_PATH_2`

## When you accidentally deleted a file, or you want to work from an older copy of a file

### Useful commands

- `git checkout $COMMIT $FILE_PATH`

## When something changed, everything exploded, and you need to go back to happier times

### Useful commands

- `git revert $COMMIT`

## When you're feeling particularly courageous (see synonym: foolish) and you want to do things that can never be undone

### Useful commands

- `git reset --hard $COMMIT` **!!!!!**

# Making real life use of history

## Solo work

When working solo projects, git history is mostly useful for the purpose of protecting
yourself from yourself. Common mishaps, such as:

- Oops, I didn't mean to delete that file
- Ok so I changed this file to do this thing differently, but turns out I liked the first way more
- That changed seemd ok when I tested it, but everyting just exploded when I deployed it

are easily addressed by maintaining a good commit history, and knowing how to navigate it. Less common,
but equally practical benefits of maintaining quality git history for your solo projects include:

- **Introducing collaborators**: If someone later joins you in contributing to the project, you are
  immediately reaping the benefits of using git history on collaborative projects (for spoilers, see ensuing section)
- **Handing off your project**: If someone else has to pick up the baton from you, their life will be about a billion
  times easier with quality change history to refer to

## Collaboration

When collaborating with others, the most valuable benefit provided by building quality git
history derives from the fact that every change will have 3 crucial pieces of information
attached to it:

1. What changed
2. Who changed it
3. Why was it changed

For anyone with experience collaborating with others, the pragmatic value of having this
information available for every single change ever made to a project is self-evident.
