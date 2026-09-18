# Show File from Branch in Git

This is an interesting one I learned while setting up a `/draft-gitlab-release` skill. Since I manually bump version numbers in this project, it's important to compare the live version number first, so I don't accidentally double-bump the version number on `development`.

I normally use `git checkout master && cat box.json | grep version` to quickly check the version number. However, this is a bit unwieldy as it requires switching branches, and often requires stashing my local changes as well.

In drafting this skill, GitHub Copilot recommended the `git show` command instead. The syntax is:

```bash
git show <branch_name>:<file_path>
```

This will display the contents of the specified file from the specified branch without checking out the branch at all!

Using this and `jq` to parse the version numbers, I can quickly compare version numbers between `development` and `main`:

```bash
developmentVersion="$(jq -r '.version' box.json)"
mainVersion="$(git show main:box.json | jq -r '.version')"
```
