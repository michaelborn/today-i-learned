# Override Vim Indentation Settings for a Specific Filetype

I'm working on a project which has thousands of lines of Coldfusion written with tabs. (Now's not the time to start that argument again!) I'm obviously not keen on throwing 2 spaces in the mix for indentation, so I looked up a way to override indentation for `.cfm` and `.cfc` files only.

It sounds like there are a few [different][1] ways to do this, but the easiest way is adding this line at the bottom of your `~/.vimrc/`.

```
autocmd FileType cfml setlocal tabstop=8 shiftwidth=4 softtabstop=4 noexpandtab
```

You may want to run `:h tabstop` in vim and read the notes about best practices for indentation. I did. :)

Here's the [ubiquitious SO answer][2], and here's the [Coldfusion syntax highlighter vim plugin][3] I'm using.

[1]: https://stackoverflow.com/a/159066/1525594
[2]: https://stackoverflow.com/a/30114038/1525594
[3]: https://github.com/ernstvanderlinden/vim-coldfusion
