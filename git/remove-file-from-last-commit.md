# Remove File From Last Git Commit

Ach! I over-committed! (heh, heh, joke, joke.)

I made one big commit instead of two smaller ones. Here's how to fix that:

```bash
git reset --soft HEAD^
```

Now un-stage the file you accidentally committed:

```bash
git reset HEAD MyFile
```

Now re-commit. I forgot to do this, but you can even "re-use the same commit message" by using the `-c` flag.

```bash
git commit -c ORIG_HEAD
```

[1]:https://stackoverflow.com/questions/12481639/remove-files-from-git-commit