# Escape ANSI Sequences in Bash

So after writing [all about my fancy new shell prompt][1], I had to adjust it a little. I knew I'd gotten it wrong when I started seeing my shell commands wrap **before they reached the end of the window**.

A few Google searches found me, as always, in a Stack Overflow article: ["Terminal Prompt Not Wrapping Correctly"][2], which had the [solution enclosed][3].

## Escape your ANSI Escape Codes!

Apparantely, despite being called [ANSI "Escape" Codes][4], you still need to escape these babies or weird things will happen.

## My Original Shell Prompt

Here's what I originally had for my shell prompt.

```bash
PS1="\033[0;31m$ \e[0m"
```

## Correctly Escaping the Color Codes

Here's the "proper", correctly escaped prompt. Notice I also escaped the dollar sign!

```bash
PS1="\[\033[0;31m\]\$ \[\e[0m\]"
```

## Fancier Colors

I decided to add the CWD, or Current Working Directory, back in to my prompt. Context is key! While I was at it, I moved the color codes into variables so the prompt can be more easily read. Here's the result.

```bash
PURPLE="\033[0;31m"
RED="\033[0;35m"
DIR="\W"
COLOR_RESET="\[\e[m"
PS1="\[$PURPLE\]$DIR\[$COLOR_RESET\]\[$RED\]\$\[$COLOR_RESET\] "
```

Notice the begin and ending escape characters `\[` and `\]` around each color variable.

[1]:https://github.com/mborn319/today-i-learned/blob/master/bash/make-a-custom-shell-prompt.md
[2]:https://unix.stackexchange.com/questions/105958/terminal-prompt-not-wrapping-correctly
[3]:https://unix.stackexchange.com/a/105974
[4]:https://en.wikipedia.org/wiki/ANSI_escape_code