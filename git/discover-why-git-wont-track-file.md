# Discover Why Git Won't Track a File

This was frustrating. I couldn't track changes to multiple files buried in a folder!

Again, [Stack Overflow to the rescue][1]. Use `git check-ignore -v <filename>` to see why your changes are being ignored.

```bash
git check-ignore -v plugins/myfolder
```

This should spit a `.gitignore` filepath, or some other reason why your file has been ignored. In my case, it even worked with a broken submodule, which was the root cause I couldn't track/commit changes.

**PS. Turns out this [awesome fellow][2], after initially answering the question with a "Nope, sorry, not supported" wrote [`git check-ignore`][3] to support this functionality. Where else do you get such help?**

[1]: https://stackoverflow.com/questions/12144633/which-gitignore-rule-is-ignoring-my-file
[2]: https://stackoverflow.com/users/179332/adam-spiers
[3]: https://git-scm.com/docs/git-check-ignore