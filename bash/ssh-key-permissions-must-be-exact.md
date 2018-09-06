# SSH Key Permissions Must Be Exact!

So, I just re-installed Ubuntu on my dev machine. (18.04, whoop whoop!)

One of the steps I took to make it easier was creating a private repo with all my SSH keys in it, and backing it up to Bitbucket. When I attempted to reuse this repo, I kept getting a `refused` error.

```bash
sign_and_send_pubkey: signing failed: agent refused operation
```

I eventually realized that the key files I'd copied back into place, as well as the SSH config file itself, must have certain read-only permissions applied or they will be ignored by the SSH service.

I quickly found this SO post which outlined the proper permissions: [SO: Permissions on Private Key in SSH Folder[1]. I would think it should be obvious that something as sensitive as SSH keys should be readable to only the owner. Yet, here I was!

The easy fix:

```bash
$ chmod 600 ~/.ssh/*
$ chmod 644 ~/.ssh/*.pub
```

All set! Just to make sure, I ran `ssh-add` immediately after resolving the permissions.

[1]: https://superuser.com/questions/215504/permissions-on-private-key-in-ssh-folder
