# Hide Empty Sidebars From Template

My Foundation theme was showing the sidebar even when the sidebar was totally empty. This caused some wonky-looking main content which was shifted to the left, making room for the useless (and invisible) sidebar.

The sidebar is rendered with `sidebar.php` in the theme's root folder.

```html
<aside class="sidebar cell medium-4">
	<?php dynamic_sidebar( 'sidebar-widgets' ); ?>
</aside>
```

To hide the odd-looking "invisible sidebar", I wrapped an if statement for `is_active_sidebar()` around the sidebar. The [wordpress docs][1] make it fairly obvious that this function returns a boolean indicating whether or not the sidebar has content in it.

```html
<?php if ( is_active_sidebar( 'sidebar-widgets' ) ) { ?>
<aside class="sidebar cell medium-4">
	<?php dynamic_sidebar( 'sidebar-widgets' ); ?>
</aside>
<?php } ?>
```

Done! Sidebar hides now, and the main content can now expand to fill its container.

[1]:https://codex.wordpress.org/Function_Reference/is_active_sidebar