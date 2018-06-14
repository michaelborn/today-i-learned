# Delete a Remote Branch

No explaning here. I've got a branch in my repo, want to get rid of it.

```bash
git branch -d <remote> <branch_name>
```

I'm trying to get rid of this old `agent-system` branch, so:

```bash
git branch -d origin agent-system
```

Thanks to [this massive StackOverflow answer by Matthew Rankin and Michael Johnson][1].

[1]: https://stackoverflow.com/a/2003515