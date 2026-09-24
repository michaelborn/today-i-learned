# TIL: Bash Syntax for Inline Conditionals

Despite the last 15+ years running Ubuntu as my daily driver, I don't spend much time scripting in Bash. Yesterday while working on a [git release prep skill](../git/git-show-file-from-branch.md), I found myself wondering how to compare version numbers in an inline conditional statement, without resorting to a full `if[...];then...fi` block.

Well, here it is:

```bash
[[ $developmentVersion == $mainVersion ]]; echo $?
```

In my case, this echoes `1` indicating the two values are not equal. For equal values, a `0` is echoed.

Note that the double-brace syntax (`[[...]]`) is Bash-specific, as is the double-equals sign (`==`), so make sure to use a Bash shebang in your bash scripts:

```bash
#!/bin/bash
```

For standard POSIX syntax, we would use:

```bash
[ "$developmentVersion" = "$mainVersion" ]; echo $?
```

And [here's the source for ya...][1].

[1]: https://stackoverflow.com/a/40431336