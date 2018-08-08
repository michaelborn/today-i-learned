# Convert Putty (PPK) SSH key file to OpenSSH key file

See the [quick tutorial on SuperUser][1].

## Step One: Install Putty

You need putty, or at least the tools that come with it.

```
$ brew install putty 
$ # OR
$ sudo apt install putty
```

## Step Two: Generate OpenSSH Key Files

Generate the private key from the PPK file:

```
$ puttygen mborn.ppk -O private-openssh -o ~/.ssh/myKey
```

Generate the public key from the PPK file:

```
$ puttygen mborn.ppk -O public-openssh -o ~/.ssh/myKey.pub
```

## Step Three: Allow `ssh-dss` Key Format

For whatever reason, Putty seems to only support generating a key file in DSS format. This causes an error something like this (use the `-v` flag to display verbose errors in ssh):

```
Skipping ssh-dss key /Users/me/.ssh/myKey - not in PubkeyAcceptedKeyTypes
```

This is because [the ssh-dss key format was disabled in OpenSSH 7.0][2]. To re-enable `ssh-dss`, add the following to your `~/.ssh/config` file OR your global `/etc/ssh/ssh_config` file. ([Thanks to gryphonitsolutions for the tip][3].)

```
PubkeyAcceptedKeyTypes=+ssh-dss
```

(ps. I would love pointers on how to convert a PPK to RSA instead of DSS! This would save us from any issues with this step.)

## Step Four: Reload SSH Service

You may need to restart the SSH service if you made config updates in `/etc/ssh/ssh_config` instead of your local config file:

```
$ sudo launchctl stop com.openssh.sshd
$ sudo launchctl start com.openssh.sshd
```

[1]: https://superuser.com/questions/232362/how-to-convert-ppk-key-to-openssh-key-under-linux
[2]: https://www.gentoo.org/support/news-items/2015-08-13-openssh-weak-keys.html
[3]: https://www.digitalocean.com/community/questions/ssh-refused-sshd-2444-userauth_pubkey-key-type-ssh-dss-not-in-pubkeyacceptedkeytypes-preauth