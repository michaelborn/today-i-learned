# Firefox Can't Wrap Flex Elements In Print

Wow! This was a royal pain. See [Mozilla bug report][1] for Firefox print mode.

The fix: Change `display: flex` to `display: block`. Too bad about your flexbox, but in print mode readability is more important than design and layout.

Luckily, almost every instance of `display: flex` is from [Foundation's new XY Grid][2], so it's fairly easy to disable `flex` grids everywhere on the site by simply overriding the `grid-x` or `grid-y` classes.

```css
@media print {
    .grid-x, .grid-y {
        display: block;
    }
}
```

For a more powerful use case, we may want to disable this print helper for certain elements. Use `.grid-printable` to disable this override.

```css
@media print {
    .grid-x:not(.grid-printable),
    .grid-y:not(.grid-printable) {
        display: block;
    }
}
```

Finally, if we override the grids in print, and force grid cells to fall below each other, we should make them full width and align the text to the left just in case.

```css
@media print {
    .grid-x:not(.grid-printable),
    .grid-y:not(.grid-printable) {
        display: block;
    }
    .grid-x:not(.grid-printable) > .cell,
    .grid-y:not(.grid-printable) > .cell {
        width: 100%;
        text-align: left;
    }
}
```

With luck, this may eventually make it into Foundation 6.

[1]: https://bugzilla.mozilla.org/show_bug.cgi?id=939897
[2]: https://foundation.zurb.com/sites/docs/xy-grid.html