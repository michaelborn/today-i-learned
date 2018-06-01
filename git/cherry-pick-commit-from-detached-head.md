# Cherry Pick a Commit from a Detached Head

## The Setup

I was in a `HEAD detached` state because I was working inside a submodule.

I ran `git add` and `git commit` to record my changes. Then I realized "No! I'm working in a detached head! How can I "move" my commit to the master branch?"

## The Fix

Start by checking out the `master` branch.

```bash
git checkout master
```

Then run `git reflog` to [show all branch history, not just the current branch history][1].

```bash
git reflog
```

Search for the commit you just made. (Should be at the top of the log.)

Now `cherry-pick` that commit into the current branch.

```bash
git cherry-pick 1x3Zy1
```

Done! Hooray, it worked! Thanks to [Stack Overflow][1] again.

[1]: https://stackoverflow.com/q/17857723
[2]: https://stackoverflow.com/a/15774498