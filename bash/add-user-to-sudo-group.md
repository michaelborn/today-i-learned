# Adding My Developer User to the Sudo Group

Yo, ever seen this?

```bash
[sudo] password for developer: 
developer is not in the sudoers file.  This incident will be reported.
```

The obvious reason is that your user account is not allowed to run `sudo`.

First, you'll need to log in as `root`. You can't upgrade your account to run `sudo` if you can't run `sudo` in the first place! ;)

You can use `visudo` or a few other less-recommended methods, (hand-editing `/etc/sudoers`, anyone?) but the best option I found was to add my account to the `sudo` group.

```bash
sudo adduser developer sudo
```

Now log out, and log back in as `developer`. Done!

See the [StackOverflow post][1] as well as the [Ubuntu docs][2] on the subject.

[1]: https://askubuntu.com/a/7484/103306
[2]: https://help.ubuntu.com/community/RootSudo#Allowing_other_users_to_run_sudo
