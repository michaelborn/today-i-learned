# Check for Empty String in Bash

So, I'm grabbing argument number three.

```bash
curl_data=$3
```

How do I know if the user provided this at all?

[Stack Overflow wins again][1]:

```bash
if [[ -z $curl_data ]]; then
```

This is in the `man` page for Bash, by the way.

```
-z string
      True if the length of string is zero.
```

[1]:https://serverfault.com/questions/7503/how-to-determine-if-a-bash-variable-is-empty
