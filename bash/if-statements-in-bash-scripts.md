# If Statements In Bash Scripts

Ok, so this is nothing mind-blowing. I may spend a lot of time in bash, but very little of that goes into writing scripts. Well, today I was downloading websites using a [`wget` script I wrote][1] specifically for that purpose, and had to add an if statement to construct some conditional `wget` arguments.

Here's how I thought a bash / shell if statement would work. (I confess, I did have to Google this one, and found a [great article with examples][2].)

```bash
if [ $WGET_OPTS -eq 1 ] then
  // blabla
fi
```

This threw an error!

Here is the correct syntax:

```bash
if [ $WGET_OPTS -eq 1 ]
then
  // blabla
fi
```

Today I Learned: If statements in shell scripts require the `then` keyword to be on a separate line.

(As a sidenote, this should be considered under the age-old question: ["Should curly braces appear on their own line?"][3])

[1]:https://bitbucket.org/snippets/mbornBCG/6eG6kn
[2]:http://bencane.com/2014/01/27/8-examples-of-bash-if-statements-to-get-you-started/
[3]:https://softwareengineering.stackexchange.com/questions/2715/should-curly-braces-appear-on-their-own-line
