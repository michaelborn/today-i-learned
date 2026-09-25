# TIL: How to Remove (Unset) an Apt Repository

I was installing [TablePlus](https://tableplus.com/) this morning and accidentally followed the instructions for Ubuntu 26.04. This included running this command to install the TablePlus apt repostory for Ubuntu 26.xx:

```sh
sudo add-apt-repository "deb [arch=amd64] https://deb.tableplus.com/debian/26 tableplus main"
```

Thankfully, I realized my mistake before finishing the install. But now, how would I remove this apt repo from my settings so I could install the correct version?

A quick Perplexity Q/A later, I had my answer: prefix the last command with `--remove`:

```sh
sudo add-apt-repository --remove "deb [arch=amd64] https://deb.tableplus.com/debian/26 tableplus main"
```

Once this was done, I was able to install the correct apt repository and continue with my install.