# How To Load Composer Packages from a VCS Repo

So, I'm building a Formstack API extension for the marvelous [Bolt CMS][1], and I decided to use Josh Gulledge's ['FormStackAPI` PHP integration][2].

The thing with Bolt CMS is that it uses its own (Satis) package repository for Composer, and it disables the use of the standard packagist.org repos. This means packages must be loaded from the Bolt marketplace, or else manually via a `repositories` entry.

So I have the choice to either include the package source in my repo, or link to it via a special `vcs` repository setting in `composer.json`. I chose the latter.

```
"repositories": {
  "fstackapi_php-git-repo": {
    "type":"vcs",
    "url":"https://github.com/jgulledge19/FormStackAPI"
  }
}
```

[1]: https://bolt.cm/
[2]: https://github.com/jgulledge19/FormStackAPI
