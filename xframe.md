Secure Nginx web server from Clickjacking with X-FRAME-OPTIONS

The X-Frame-Options header is a security header that Nginx (and other web servers) can utilize to prevent clickjacking attacks. An attacker uses clickjacking to deceive a user into clicking on a maliciously constructed page that is hidden behind an invisible or disguised iframe on a legitimate website.

You can use the X-Frame-Options header to specify whether your website can be loaded within an iframe on another domain. You may protect your users by specifying the right value for this header, which prevents your website from being embedded in iframes on harmful or illegal domains.

Certainly! There are a couple of ways to include the X-Frame-Options header with a valid directive in Nginx. The following are valid directive options:

DENY Directive: This directive blocks any domain from loading your website in an iframe. It is the hardest method of combating clickjacking violence.
```
add_header X-Frame-Options "DENY";
```

SAMEORIGIN Directive: With this directive, your website can only be loaded in an iframe if the parent document is from the same origin (same domain). It allows for some flexibility while also protecting your website against cross-origin framing assaults.
```
add_header X-Frame-Options "SAMEORIGIN";
```

Policy on Content Security (CSP) The Frame-Ancients Directive: This directive is preferred for current browsers since it gives you more flexibility over frame options. It enables you to create a Content Security Policy that determines which domains are allowed to embed your website in an iframe.
```
add_header Content-Security-Policy "frame-ancestors 'self' example.com;";
```

Change 'example.com' to the domain(s) you want to enable to embed your website in an iframe. Multiple domains separated by spaces can be added.

Select the right directive option depending on your individual needs and security concerns. Once you've decided, insert the corresponding 'add_header' directive into the appropriate Nginx server block. To make the changes take effect, save the configuration file and restart Nginx.

Remember to adapt the settings to the relevant server block and make sure you have permission to alter Nginx's configuration files.

You can allow multiple domains in the Content-Security-Policy (CSP) frame-ancestors directive. This lets you define numerous domains that can include your website in an iframe. Here's an example of how to allow multiple domains using the CSP frame-ancestors directive:
```
add_header Content-Security-Policy "frame-ancestors 'self' domain1.com domain2.com;";
```
