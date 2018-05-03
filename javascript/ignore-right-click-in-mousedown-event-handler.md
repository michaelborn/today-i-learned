# Ignore Right-click Events in a `mousedown` Event Handler

Making a "Print page" button. You know the drill. Use `addEventListener()`, pass a callback function.

```js
document.getElementById("btnPrint").addEventListener("mousedown",printWindow);
```

Here's my event handler:


```js
var printWindow = function(e) {
    window.print();
};
```

Once I right-clicked on the button to inspect it, I realized it would be nice to NOT open the print dialog if the user right-clicks on it for some/any reason. This would make more sense for a larger element, but whatever.

Here's my ubiquitous, [ever-so-relevant Stack Overflow answer by FriendlyGuy][1], and the slightly more referential [MDN post describing the `MouseEvent.button` event handler parameter][2].

```js
var printWindow = function(e) {
    var isLeftMouseButton = function() { return e.button === 0; };
    if ( isLeftMouseButton() ) {
        window.print();
    }
};
```

Ta-da!

[1]: https://stackoverflow.com/a/9521965
[2]: https://developer.mozilla.org/en-US/docs/Web/API/MouseEvent/button