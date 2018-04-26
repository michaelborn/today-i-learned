#  Make a Short Bash Prompt

Ok, so I use [VS Code][1] with an integrated terminal on the right. My terminal is **really** narrow, so I run out of room quickly. My bash  prompt can overflow the narrow screen, so I decided to change it.

Following [this article about changing the bash prompt][2], I set the `PS1` variable to this:

```bash
PS1="\033[0;31m$ \e[0m"
```

The `\e033[0;31m` [ANSI escape sequence stands for red][3], and the `\e\0m` sequence resets the color, leaving my prompt as a super-short:

```bash
$
```

[1]:https://code.visualstudio.com/docs/editor/integrated-terminal
[2]:https://www.cyberciti.biz/faq/bash-shell-change-the-color-of-my-shell-prompt-under-linux-or-unix/
[3]:https://stackoverflow.com/a/28938235
