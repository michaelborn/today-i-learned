# Cron Jobs Have Different `$_SERVER` Globals

So, I was getting this error message in a new cron job / nightly import I'd set up.

```
Warning: require_once(/my/path/db.php): failed to open stream: No such file or directory in /home/bla/public_html/my/init.php on line 18
```

My code looked something like this:

```php
require_once($_SERVER['DOCUMENT_ROOT'] . '/my/path/db.php');
```

This made no sense to me! I'd tested this script manually in the browser multiple times when I set up this import. Why does it fail only for the cron job?

I did some googling for "PHP Cron Job Include Fail" and eventually came across [this SO post][1] which has enough detail to explain the issue:

> Assuming you are running the script directly through cron (as opposed to from a web server accessed by an HTTP request triggered by a cronjob (e.g. by cron running wget)), then of course it doesn't work.
> There is no server, so $_SERVER is not set.

I guess this should have been obvious, but from my CFML background it was not. CFML scheduled tasks are run in the same context as any normal page request, whereas cron jobs for PHP scripts have to run a little differently because they rely on the Linux cron job functionality. Quentin's answer makes this a little more obvious by pointing out the alternative: running the PHP script via calling the url through `wget`.

[1]: https://stackoverflow.com/a/2100577