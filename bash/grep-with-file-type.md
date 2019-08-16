# TIL: How to Grep For a String In .cfc File Type

Need to change a variable name across 50 files in 10 folders? Here's how to grep for that variable in `.cfc` files:

```bash
grep -r -i --include \*.cfc 'wirebox' modules
```

What a neat trick! I googled this today and couldn't believe my awesome luck. The last time I had to do this I think I used `locate`, like this:

```bash
locate -type f -name '*.cfc' modules| grep -i 'wirebox'
```

As you can see, the `grep --include \*.cfc` is a far cleaner syntax.

Once again, here's the SO post with the answer: https://stackoverflow.com/questions/12516937/grep-but-only-certain-file-extensions