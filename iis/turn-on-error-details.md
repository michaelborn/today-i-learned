# Turn On Error Details In IIS

Ran into this today. Debugging a Coldfusion app on IIS, I'm having trouble getting any errors, despite having a nice Coldfusion error handler set up.

Turns out IIS was supressing these errors for security reasons. Nice for production, until you need to debug.

## One: Add `<customErrors mode="Off" />` to `<system.web>`

```xml
<system.web>
	<customErrors mode="Off" />
</system.web>
```

## Two: Add `<httpErrors errorMode="Detailed" />` to `<system.webServer>`

```xml
<system.webServer>
    <httpErrors errorMode="Detailed" /> 
</system.webServer>
```

## Full `web.config` XML

And that's it! Here's my whole `web.config` for posterity.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
	<system.web>
		<customErrors mode="Off" />
	</system.web>
    <system.webServer>
        <httpErrors errorMode="Detailed" /> 
    </system.webServer>
</configuration>
```

Source: [Jim Tollan][1] and [Kasper Halvas Jensen][2] on Stack Overflow

[1]:https://stackoverflow.com/a/11665456
[2]:https://stackoverflow.com/questions/11665322/how-to-set-web-config-file-to-show-full-error-message#comment66285857_11665456