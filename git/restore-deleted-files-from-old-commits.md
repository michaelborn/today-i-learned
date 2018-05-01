# Restore Deleted Files from Older Commits

Ugh. So I saw a bug logged today due to a missing piece of code. What?! That was there yesterday! Turns out I had deleted the file by accident and not realized it.

## Find the Commit Which Deleted the File

This article talks about [How to find and restore deleted files with git][1], and wonderfully explains the first step: discovering the offending git commit.

```bash
git log --diff-filter=D --summary
```

This will give you a log of all commits which deleted a file. The `--summary` will also show which files were deleted.

## Restore the file from the commit

Given commit ID `123x7x`, run this to restore the file(s)

```bash
git checkout 123x7x~1 myFile
```

There's also a score of great answers on [this StackOverflow question][2] as well.

[1]:http://blog.kablamo.org/2013/12/08/git-restore/
[2]:https://stackoverflow.com/questions/953481/find-and-restore-a-deleted-file-in-a-git-repository