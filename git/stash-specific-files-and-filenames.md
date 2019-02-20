# Stash Specific Files and Filenames

Why would you ever want to stash a specific file, as opposed to any and all altered files, you ask? In an ideal world, you probably wouldn't need to. In this specific case, I was attempting to stash files I had modified without stashing other files which had been bulk-edited by a script. In other words, I wished to throw away _most_ of my changes and keep one or two specific changes after a `git merge`.

See [this question][1], of which the [accepted answer][2] is pretty darn useful:

> Since git 2.13, there is a command to save a specific path to the stash: git stash push <path>. For example: git stash push -m welcome_cart app/views/cart/welcome.thtml.

Boom:

```
git stash push <path>
```

[1]: https://stackoverflow.com/questions/5506339/how-can-i-git-stash-a-specific-file/5506483#5506483
[2]: https://stackoverflow.com/a/5506483/1525594