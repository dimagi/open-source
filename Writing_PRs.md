# PR Title

Used for:

* Reading through the deploy email to guess which PR caused a bug
* Tracking down a change possibly months or years in the future
* Putting together a summary of recent changes for global services or external users

Choose a reader-friendly title, and consider the multiple audiences that may
want to know what it concerns.


# PR Description 

Describe what the PR accomplishes at a high-level, including anything that would
help give context to the reader:

* Links to the fogbugz ticket, trello card, error log, or spec doc
* Screenshots - anything user-facing should include a screenshot. Make sure you
  know the keyboard shortcut to copy a portion of your screen to the clipboard
  so you can paste it directly in github.
    - Ubuntu: Shift+Ctrl+PrtSc
    - Mac: Ctrl+Shift+Cmd+4
    - Windows: Windows+Shift+S or "Snipping Tool"
* Information about the scope of the change - what does this affect?
* Tips for reviewers, such as suggesting they read commit-by-commit or view
  something with whitespace ignored
* Spend a time proportionate to the size of the PR writing a description and/or notes.
    * Cory: "If you worked for a week on something it's probably good to spend
      hours explaining it in the PR"
* Cory: "For complex code I like to do the first review myself, where I walk
  through the whole PR and make comments on anything I see that is not obvious /
  jumps out. Good to do this while the code is still fresh in your mind and will
  make things easier for the reviewer. Also in this process think about whether
  a code comment makes more sense than a PR comment and add them."

Remember that people _will_ come across this PR with no understanding of the
background that led to this change, so be sure to provide it for them.

Here's an example that hits many of these points and is nicely formatted for reading:
https://github.com/dimagi/commcare-hq/pull/20874

# What to PR

* Pull requests should be discrete.  That is, they should cover one topic.
* If you can split up a series of changes into multiple PRs, consider doing so.
* Feature additions which are somewhat independent of the original scope of the
  PR should be PR'd separately into the main PR.  More on this below:

### Very large changes that can't be merged in smaller chunks

Sometimes you'll build a large new feature or refactor that needs to be merged
all in one go.  First consider whether you can safely develop behind a feature
flag, allowing you to merge regularly into master.

In practice, this often starts out with a relatively clean PR, but then comes a
lot of back-and-forth on small changes, and meanwhile, you're working on other
aspects of that feature, so you push those changes too, and before you know it,
the PR has 3000 lines changed and is 200 commits long.  Now no one can review
it except as a whole, but it's impossible to do so meaningfully.

Instead, make child PRs for each non-trivial addition. Here's a recent example
where I did this: https://github.com/dimagi/commcare-hq/pull/21092

1. Make a PR with the primary changes and begin the review process.
1. As you finish associated features, open those as separate PRs with the base
   branch as your main feature branch.
1. At some point, you'll need to stop adding commits directly to the main
   branch.  Do this before merging any child PRs, or after reviewers have
   signed off on the main PR.  The reviewers should no longer need to review
   the main PR at all.
1. Once all the necessary child branches have been approved and merged into the
   main branch, you can merge that in at a time where you'll be able to monitor
   its rollout.
1. If you have straggler child PRs that aren't blocking, you can merge the main
   PR anyways, and switch the base branch of those child PRs to `master`


# Clean git histories, or "How to pretend you don't make mistakes"

* Before opening PR, organize commits into reviewable chunks
* Try very hard to do mechanical changes in separate commits from thoughtful
  changes, and make it clear which is which. Don't make reviewers play "spot
  the differences".
    * Rename a file, then refactor it in a separate commit.
    * Move functions around, then refactor them in a separate commit.
    * If a PR has substantial linting, do that in a separate commit, possibly a
      separate commit for each kind of lint
* Fixup little "oops" commits, they're distracting. Use
  [`rebase.autosquash`](https://robots.thoughtbot.com/autosquashing-git-commits)
  to streamline this process.
* Squash comments together with the relevant code
    * Jenny: "When working, I often do a pass at the end adding comments and
      then fixup-ing them into other commits"
* Use verbose, sometimes multi-line commit messages
* Lint on your own, before you PR.
* Once people have begun reviewing the PR, refrain from messing with the commit history.
* It's fine to have a few one-or-two-line commits **after the PR is opened** for
  linting and nitpicky feedback, these are quick to review
* Larger restructuring should be cleanly committed


# Git training wheels and safety nets

### As-you-go tips to make your history easier to manage:

* Commit your changes in meaningful chunks (not `git add .`)
* Try making small commits you can rearrange and squash later.
* Use a diff tool or at least `git add -p`
* `git commit --amend` your last commit when applicable

### Worry-free handling of a big restructure:

* If you're feeling paranoid, make a backup branch:
    * `git branch es/mybranch-backup`
* `git rebase --abort` and `git merge --abort`
* `git reflog` - See all recent commits, in case you lost one
* Set your .gitconfig to prevent you from accidentally deleting a commit during rebase

```ini
[rebase]
    missingCommitsCheck = error
```


# Cherry-picking

* Great way to pull out independent changes encountered in the middle of a big PR.
* This lets you get in some changes ASAP, without being blocked on a big PR.  It also helps make that big PR a bit smaller

### Workflow:

1. Make a commit with just the changes you want to pull out. Make a note of the
   commit hash
1. Save the rest of your changes in a WIP commit or come back to this after you
   get to a good stopping point
1. Checkout a new branch from origin/master, then `git cherry-pick abc123`
1. Open a PR
1. When preparing your main branch for PR:
1. If that first PR has made it to master, `git rebase origin/master` will
   automatically drop it from your main branch
1. If that first PR isn't merged and that commit is fully independent, you can
   drop it manually in a rebase (covered later)
1. If that first PR isn't merged and you need that commit, just leave it in - at
   least you tried


# Rebasing - the reBASICS

You provide a target branch. Git will take all your commits not already on that
branch, and add them on top of it.

This gets rid of merge commits, and will drop any commits that are already on master.

It's similar to cherry-picking, except with a string of commits, rather than just one

Interactive rebasing gives you fine-grained control over how those commits are
applied. Read `man git-rebase` for a great overview (search for `INTERACTIVE
MODE`).

```
# Commands:
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
# d, drop = remove commit
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# Do not remove any line. Use 'drop' explicitly to remove a commit.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```

Note that the without `missingCommitsCheck = error`, this says

```
# If you remove a line here THAT COMMIT WILL BE LOST.
```


# Iteractive Rebasing

```bash
$ git rebase -i origin/master
```

```
pick 6a6e24cbd9 Copy mpr_3ii_person-cases.json
pick f55eebb0ce Run cleanup script on mpr3 report
pick 38d54b1457 Replace dynamic filters with static ones
pick 8586c7f05e field isn't applicable for this column type
pick c546c3e10b Also aggregate by age group
pick c546c3e10b Remove trailing comma from filter

# Rebase ea1c24e1d8..c546c3e10b onto ea1c24e1d8 (5 commands)
#
# Commands:
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
# d, drop = remove commit
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# Do not remove any line. Use 'drop' explicitly to remove a commit.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```

Let's say I'd rather move commit 4 to right after commit 2, and merge the changes from the last commit into two commits before it:

```
pick 6a6e24cbd9 Copy mpr_3ii_person-cases.json
pick f55eebb0ce Run cleanup script on mpr3 report
pick 8586c7f05e field isn't applicable for this column type
pick 38d54b1457 Replace dynamic filters with static ones
f c546c3e10b Remove trailing comma from filter
pick c546c3e10b Also aggregate by age group
```

# Rebase examples

Maybe you want to modify _your_ commits, without necessarily incorporating those from origin/master:

```bash
$ git merge-base $(git rev-parse --abbrev-ref HEAD) origin/master
```

Or stick this in your .gitconfig:

```ini
[alias]
    current-branch = rev-parse --abbrev-ref HEAD
    last-master-commit = "!git merge-base $(git current-branch) origin/master"
    rebase-new-commits = "!git rebase -i $(git last-master-commit)"
```

Let's say you have a PR that's already been reviewed, and you're assembling some
additional changes to push. You probably don't want to rebase the whole PR.
Instead, only rebase the changes that haven't yet been reviewed:

```bash
$ git log HEAD --pretty=oneline --not origin/master
fe7de0f50b (HEAD -> es/icds-mobile-reports) whoops, typo
c546c3e10b Also aggregate by age group
ff76e5d0f1 lint
38d54b1457 (origin/pull/21803, origin/es/doc-conditional-aggs) Replace dynamic filters with static ones
8586c7f05e field isn't applicable for this column type
f55eebb0ce Run cleanup script on mpr3 report
6a6e24cbd9 Copy mpr_3ii_person-cases.json
```

Rebase since a particular commit

```bash
$ git rebase -i 38d54b1457
```

Or rebase the last 3 commits:

```bash
$ git rebase -i HEAD~3
```


# Other resources

* https://learngitbranching.js.org
* https://try.github.io
* https://chris.beams.io/posts/git-commit/
