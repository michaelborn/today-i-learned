# Override Login Messages with `add_filter()`

Using the Wordpress ["Theme My Login"][1] plugin to display a nice login form on a custom dashboard page. The form by default displays a "Log In" message, but what I'd like to see is "Please log in to view your application status".

## What Is `apply_filters()`

[Under the hood][2], the plugin uses `apply_filters(...)` to allow customizing the login message.

```php
return apply_filters('tml_action_template_message', $message, $action);
```

## Using `add_filter()`

To modify it, one needs only call `add_filter( $filter_name, $func_name, $priority, $arg_count )` where `$filter_name` is `tml_action_template_message` and `$func_name` should be the name of a function which will return the new string for the login message. While `$priority` was not important in my case, for me it was important to pass `2` for the `$arg_count` or [else I wouldn't receive both arguments][3] passed from the original `apply_filters()` call.

```php
add_filter( 'tml_action_template_message', 'custom_dashboard_login_message', 10, 2);
```

## My Filter Function

The function called needs only return a string. It could be the same string every time, or it could differ based on URL variables, time of day, various arguments, etc.

```php
function custom_dashboard_login_message( $message, $action = '' ) {
    if ( $action === 'login' ) {
        $message = 'Please log in to view your application status.';
    }
    return $message;
}
```

This did the trick for me!

[1]:https://wordpress.org/plugins/theme-my-login/
[2]:https://github.com/jfarthing84/theme-my-login/blob/6.4/includes/class-theme-my-login-template.php#L413
[3]:https://stackoverflow.com/questions/24198086/missing-argument-2-for-the-function-in-wordpress