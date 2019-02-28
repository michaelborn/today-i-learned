# Ignore Linting Rules in CFLint

So, [CFLint](https://github.com/cflint/CFLint) is super useful for CF development. There's a [VS Code Extension](https://marketplace.visualstudio.com/items?itemName=KamasamaK.vscode-cflint) which can lint your CF tag or script syntax on the fly, and there is also a [CommandBox Package](https://www.forgebox.io/view/commandbox-cflint) which can lint an entire folder of `.cfm` or `.cfc` files.

CFLint has a lot of rules, some of which are useful and some of which are [less so](https://github.com/cflint/CFLint/blob/master/src/main/resources/cflint.definition.json). Here's where I figured out how to turn off the more annoying / less useful linting rules.

1. Create a `.cflintrc` file in the root of your project.
2. Paste in the following JSON:

```json
{ 
    "rule": [],
    "excludes": [],
    "includes": []
}
```

3. Add whichever rules you wish to exclude to the `excludes` array. Or, if you only wish to check for a small set of rules, add those to the `includes` array.


Here's the final result:

```json
{ 
    "rule": [],
    "excludes": [
        {
            "code": "UNQUOTED_STRUCT_KEY"
        },
        {
            "code": "LOCAL_LITERAL_VALUE_USED_TOO_OFTEN"
        }
    ],
    "includes": []
}
```