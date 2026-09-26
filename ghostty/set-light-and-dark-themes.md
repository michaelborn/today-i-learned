# TIL: Set Light and Dark Ghostty Themes

Working from a laptop has some advantages. On beautiful fall days like this one, I can unplug my display and dongles and transition to a lawn chair in the shade. There's only one problem - the ambient light outdoors (even while sitting in the shade) is too great for my Lenovo E16 to overcome.

Switching to a light theme outdoors mostly takes care of this, but I noticed my Ghostty terminal was still in dark mode.

Checking the docs, it seems Ghostty already supports auto-switching between themes based on the system appearance. All we have to do is add the following line to the Ghostty config in ` ~/.config/ghostty/config`:

```ini
theme = dark:GitHub Dark,light:GitHub Light Default
```

Now Ghostty uses GitHub Dark in dark mode and GitHub Light Default in light mode.
