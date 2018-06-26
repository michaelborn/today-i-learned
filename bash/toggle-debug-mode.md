# Toggle Debug Mode

Doing a big (ok, small) script to check for SSL certificates on a list of about 200 of our client websites.

Something like:

```bash
cat our-client-domain-list.md | xargs -n1 sslcheck
```

And `sslcheck` looks like this:

```bash

# Do curl...
RESPONSE="$(curl --HEAD --silent https://$DOMAIN)";

if [[ $RESPONSE = *"200 OK"* ]]; then
  echo -e "--- Found SSL! ---";
else
  echo -e "--- Could not find SSL ---";
fi
```

This outputs a totally useless list of success and failure notifications with zero context.

```bash
--- Could not find SSL ---
--- Found SSL! ---
--- Could not find SSL ---
```

Obviously, we need to show what domain has SSL and which does not. I thought it would be cool to output the exact `curl` command executed, instead of just printing the `$DOMAIN` variable. Here's the [Stack Overflow post][1] which mentions the `set -x` option built in to Bash. Turn on with `set -x`, turn off with `set +x`.

```bash
# turn on command "debugging", or verbose mode 
# to output the curl command when we run it. 
set -x

# Do curl...
RESPONSE="$(curl --HEAD --silent https://$DOMAIN)";
# Turn off debug mode
set +x

if [[ $RESPONSE = *"200 OK"* ]]; then
  echo -e "--- Found SSL! ---";
else
  echo -e "--- Could not find SSL ---";
fi
```

Here's the much more useful output:

```bash
++ curl --HEAD --silent https://www.site0.com
+ RESPONSE='HTTP/1.1 200 OK
Content-Length: 0
Content-Type: text/html; charset=UTF-8
...
'
+ set +x
--- Found SSL! ---
++ curl --HEAD --silent https://www.site1.org
+ RESPONSE=
+ set +x
--- Could not find SSL ---

++ curl --HEAD --silent https://www.site2.com
+ RESPONSE=
+ set +x
--- Could not find SSL ---
```

Ta-da!

[1]: https://stackoverflow.com/a/2853811