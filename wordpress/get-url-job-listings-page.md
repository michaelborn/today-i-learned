# How to get the URL of a Job Listings page

After installing [WP Job Manager][1] on a careers-focused Wordpress site, I needed to set up a job search form. This search form would allow users to enter in a job title, keyword, etc to search the jobs on the site. Clicking "Go" would bring them to the job listing page.

Aha, but where IS that proverbial Job Listings page? This page URL can be altered through the WP Job Manager settings, so you can't hardcode it! The answer lay buried in source code for the "Jobs Page" setting.

To get the ID of the job listings page, use the [`get_option` function][2] for the "job_manager_jobs_page_id" option:

```php
$jobsPageID = get_option( 'job_manager_jobs_page_id' );
```

To get the permalink of the job listings page, use the [`get_permalink` function][3].

Wrapping it all up, here's the search form:

```html
<form method="GET" action="<?php echo get_permalink(get_option( 'job_manager_jobs_page_id', false )); ?>">
...
</form>
```

[1]:https://wpjobmanager.com/
[2]:https://developer.wordpress.org/reference/functions/get_option/
[3]:https://developer.wordpress.org/reference/functions/get_permalink/
