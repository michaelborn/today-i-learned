# Highlight Search Pattern Matches in Vim

So, my machine at work is less Vim-ified than my lean, mean, Ubuntu machine at home. When I tried searching for a variable (like `/$applications`), I couldn't immediately see the matched strings, meaning I have to skip to each match with `n`.

I knew there was a way to do this, but couldn't remember how. A quick Google search brought me to `vim.wikia.com`'s super-useful ["Highlight all search pattern matches"][1] article.

In summary:

1. Open your `.vimrc` located in your home folder. `vim ~/.vimrc`
2. Add `set h1search` anywhere in the file.
3. Save and close the file. `:wq`
4. Open vim, and wallah! It works!

**Pro tip: If you like pausing Vim with `^Z` so you can Vim while you Vim, then you'll have to reload your configuration to see the change. Run `:so ~/.vimrc` in Vim to reload config. This is roughly equivalent to Bash's `source ~/.bashrc`.**

See it in my [dotfiles][2] repo.

[1]:http://vim.wikia.com/wiki/Highlight_all_search_pattern_matches
[2]:https://github.com/mborn319/dotfiles/
