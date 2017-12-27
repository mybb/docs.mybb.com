---
layout: page
title:  "Setting up HTTPS"
categories: [security]
---

# Security and privacy with TLS
<strong>TLS</strong> (<i>Transport Layer Security</i>; previously SSL, <i>Secure Sockets Layer</i>) is a set of cryptographic protocols providing encrypted connections over a computer network. The protocol used for accessing web pages, HTTP, wrapped in TLS is known as <strong>HTTPS</strong> (<i>Hypertext Transfer Protocol <u>Secure</u></i>) and is becoming the standard of the modern web &mdash; more than half of web page impressions are served using HTTPS.

TLS certificates issued by <i>certificate authorities</i> (CAs) are used for asymmetric encryption, where web browsers request the public key for a particular website to encrypt information that can be decrypted with the corresponding private key known only to the destination server, eliminating the possibility of anyone being able to read the data itself even if the whole communication is being intercepted. This results in establishing a shared key for symmetric encryption, where the encryption and decryption is being done using the same secret for optimal performance.

Most web sites and forums exchange sensitive information like passwords, IP addresses and personally identifiable information protected by law in most countries &mdash; not having all of your web site's connections secured can result in disclosure of such data in cases as simple as using public internet hotspots, which is the reason major web browsers have started delivering warnings to users when the connection security can be questioned. Modern web server software allows administrators to set up HTTPS without significant performance or compatibility drawbacks and we <strong>strongly</strong> recommend board administrators upgrade their boards to support HTTPS and enforce it.

# Obtaining a TLS certificate &amp; configuring the server
The TLS certificate for a public website needs to be issued by a certificate authority trusted by major web browsers, validating the ownership of a domain. Certificates can be obtained from CAs directly as well as domain and web hosting providers &mdash; it's possible that your host contains such offers or that it's already included in your package.

Configuring the web server to present a valid certificate depends on the operating system and platform &mdash; refer to external resources:

- <a href="https://www.digicert.com/ssl-certificate-installation.htm">How to Install an SSL Certificate (digicert.com)</a> or
- <a href="https://www.namecheap.com/support/knowledgebase/article.aspx/795/69/how-to-install-ssl-certificates">How to install SSL certificates (namecheap.com)</a>

and select the software you're using.
If you're configuring a server on your own, you need to follow <a href="https://mozilla.github.io/server-side-tls/ssl-config-generator/">common recommendations</a> of modern protocols and ciphers.

It's also possible to use <a href="https://letsencrypt.org/">Let's Encrypt</a>, an automated CA providing free certificates with comparable level of security and tools that make the setup and certificate renewal process easier &mdash; refer to <a href="https://certbot.eff.org/">certbot.eff.org</a> for installation instructions and make yourself familiar with its <a href="https://certbot.eff.org/docs/using.html">usage guide</a>.

## Reverse proxies
If your websites take advantage of reverse proxies (such as Amazon CloudFront or Cloudflare) you should set up both connections (between your users and the proxy server as well as between the proxy server and the origin server) to use HTTPS. For example, Cloudflare provides <a href="https://blog.cloudflare.com/cloudflare-ca-encryption-origin/">Origin CA</a> certificates that can be installed on your server to be able to communicate with Cloudflare securely; you can also use certificates provided by Let's Encrypt. Remeber to instruct the proxy server to always use secure connections on both sides.

# Switching and enforcing HTTPS

## MyBB settings
Update the <strong>Board URL</strong> in the ACP under <strong><i>Settings &rarr; Site Details</i></strong> to reflect the changes, replacing `http://` with `https://`.

## Protocol redirection
Once your forum works properly under the new protocol, you can set up your server to redirect your visitors to the new address.

- <strong>Apache</strong> servers:

  First, add the following line in the <strong>.htaccess</strong> file in your forum's main directory or your <i>VirtualHost</i> file if it's not already present:

  ```
  RewriteEngine On
  ```

  Following the statement, insert a rule that will redirect the traffic changing the protocol under the condition that it's not HTTPS:

  ```
  RewriteCond %{HTTPS} off
  RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
  ```

  Alternatively, if you use a reverse proxy and the connection between the proxy and your server doesn't happen over HTTPS (which is highly discouraged), you might need your server to check the value of the `X-Forwarded-Proto` header (supplied by the reverse proxy) instead:

  ```
  RewriteCond %{HTTP:X-Forwarded-Proto} !https
  RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
  ```

  Make sure this is the first redirect rule and the protocol redirection is always the first one that's performed.

- <strong>nginx</strong> servers:

  ```
  server {
      listen 80 default_server;
      listen [::]:80 default_server;
      server_name _;
      return 301 https://$host$request_uri;
    }
  ```
  ```
  if ($http_x_forwarded_proto = "http") {
      return 301 https://$server_name$request_uri;
  }
  ```

# Removing mixed content
Mixed content (insecure content) occurs when the initial page is delivered over HTTPS, but includes content (such as images, videos, etc.) downloaded through unsecure HTTP, limiting the security benefits of HTTPS (<a href="https://developer.mozilla.org/en-US/docs/Web/Security/Mixed_content#Mixed_active_content">read more</a>).

## Templates and CSS
Some resources, like images, CSS or JavaScript files might be loaded through your MyBB theme's CSS files (<strong><i>Templates & Style &rarr; Themes</i></strong>) and templates (<strong><i>Templates & Style &rarr; Templates</i></strong>). Those are usually located in the <strong>headerinclude</strong> template (<i>Ungrouped Templates</i>). You can also use the <strong>Search/Replace</strong> utility to find all occurences of `http://` to replace it with `https://`, making sure these resources work correctly under the new address first.

## User content
The usual MyBB installation inserts external content into the forum page source basing on user's input in two places:
 - <strong>avatars</strong>, when a user provides a link to an external image instead of uploading one,
 - <strong>MyCode output</strong>, when `[img]` and `[video]` tags are translated to HTML's `<img>` (images) and `<iframe>` &amp; `<embed>` (video widgets), displayed directly on the forum's pages.

As long as users provide HTTPS-based URLs to these elements browsers will render the page properly, however a single insecure element can cause browsers to block such mixed content and display a warning.

This can be aided by installing <a href="https://community.mybb.com/mods.php?action=view&pid=450"><strong>DVZ Secure Content</strong></a>, a MyBB 1.8.x plugin with two operating modes described below.

### Blocking insecure resources
A simple and straightforward way to make your forums work properly under HTTPS is blocking all elements pointed to using `http://` &mdash; simply make sure the <i>Filter non-HTTPS MyCode images</i> and <i>Block non-HTTPS avatars</i> settings are set to <strong>On</strong> under <strong><i>Configuration &rarr; Settings &rarr; DVZ Secure Content</i></strong>.
You can notify your forum's users that images and videos will be displayed if they provide `https://` URLs.

### Proxying insecure resources
It's possible to keep displaying all content securely, regardless of the protocol used with a <i>resource proxy</i>. Instead of pointing browsers to original URLs (that your forum users provide), the content can be served from your own server that first fetches it from the original server and then forwards it to the end user &mdash; always over HTTPS.

This will require a resource proxy script, best if running on a server other than your forum's (you will need a VPS or a dedicated server):

- <a href="https://github.com/atmos/camo">github.com/atmos/camo</a> for NodeJS,
- <a href="https://github.com/ankane/camo">github.com/ankane/camo</a> for Ruby

After setting up a resource proxy, configure the mentioned plugin by setting <i>Image proxy</i> to <strong><i>On</i></strong> and configure the remaining settings. An example configuration for the <i>atmos/camo</i> implementation:

- <i>Image proxy URL scheme</i>: `{PROXY_URL}{DIGEST}/{URL}`
- <i>Image proxy URL</i>: `https://camo-url.example.com/`
- <i>Image proxy key</i>: `0x24FEEDFACEDEADBEEFCAFE`
- <i>Image proxy digest algorithm</i>: `sha1`
- <i>Image proxy forwarded URL protocol</i>: <i>No changes</i>
- <i>Image proxy forwarded URL encoding</i>: <i>Hex encoding</i>

 This can vary with each implementation &mdash; if you're having problems, consult the script's documentation or <a href="https://community.mybb.com/forum-179.html">create a support thread</a>.

You can also decide whether all or HTTP resources only should be forwarded in the <i>Image proxy policy</i> and <i>Proxy avatars</i> settings.
Proxying all remote resources has positive impact on your forum users' privacy because information like the IP addresses and operating system &amp; browser-related details are revealed only to the resource proxy server (in most cases operated by the same people that operate the forum itself). Third party servers, where such resources are being stored, will only receive information related to the proxy server that relays the data further.

<hr />

After configuring your setup, use the plugin's tools available on <strong><i>Configuration &rarr; Plugins</i></strong> to secure the video widget templates and avatars &mdash; all <i>Security overview</i> indicators should read <i>Yes</i> (with the exception of <i>All remote resources proxied</i>, if you didn't decide to use a resource proxy).

## Custom MyCode
If your board takes advantage of custom MyCode tags, review the <i>Replacement</i> codes and make sure they don't load external content over the unsecured protocol.

# Security headers
Additional headers, added to every response from your server, can contain directives instructing browsers to react to security-related events in a desired fashion. You can find a more detailed list <a href="https://www.owasp.org/index.php/OWASP_Secure_Headers_Project#tab=Headers">here</a>.

**Basic security headers**

| Header name | Suggested value for MyBB | Description |
| - | - | - |
| `Strict-Transport-Security` | `max-age=31536000; includeSubDomains; preload` | Prevents the browser from downgrading connections to your website to plaintext HTTP until the `max-age` time has elapsed. If `includeSubDomains` is specified, the rule applies to all subdomains. The `preload` part instructs that this rule can be hardcoded into web browsers (<a href="https://hstspreload.appspot.com/">read more</a>). Include only if your forum is working correctly under HTTPS (you can set the `max-age` to lower periods of time and increase it afterwards). |
| `Content-Security-Policy` | `upgrade-insecure-requests; default-src https: data: 'unsafe-inline' 'unsafe-eval'` | Instructs the browser to upgrade protocols of included HTTP resources to HTTPS and to block unsecured elements. | 
| `X-Frame-Options` | `deny` | Improves the protection against clickjacking by preventing the website from being displayed in frames. |
| `X-XSS-Protection` | `1; mode=block` | Enables the browser's XSS filter. |
| `X-Content-Type-Options` | `nosniff` | Intructs the browser to interpret filetypes according to the content type header. |

The `Content-Security-Policy` can be further <a href="https://report-uri.io/home/generate">fine-tuned</a> to contain definitions of allowed sources for specified types of content and how it can be included on the website. It heavily relies on the forum's configuration and some rules are not possible (e.g. MyBB requires inline scripts to be allowed).

**Adding headers to server responses**

- On <strong>Apache</strong> servers, make sure the `mod_headers` module is enabled and add each header in a separate line to the <i>.htaccess</i> file or your <i>VirtualHost</i> file:

  ```
  Header always set HeaderName "headerValue"
  ```

  replacing <i>HeaderName</i> and <i>headerValue</i> with intended values. <a href="https://httpd.apache.org/docs/current/mod/mod_headers.html">mod_headers documentation &rarr;</a>

- On <strong>nginx</strong> servers, make sure the `ngx_http_headers_module` module is enabled and add each header in a separate line to the <i>location</i> block:

  ```
  add_header HeaderName headerValue;
  ```

  replacing <i>HeaderName</i> and <i>headerValue</i> with intended values. <a href="https://nginx.org/en/docs/http/ngx_http_headers_module.html">ngx_http_headers_module documentation &rarr;</a>

# _Secure_ cookies

Once HTTPS is configured, browsers should be informed that cookies (which contain sensitive information) should only be sent over a secure connection: set the <strong>Secure Cookie Flag</strong> setting under <strong><i>Configuration &rarr; Site Details</i></strong> to <strong>Yes</strong> (available on MyBB 1.8.9 and up).

# Subresource Integrity
If your board takes advantage of resources (such as CSS or JavaScript files) stored on remote servers like CDN providers, it's a good idea to use <strong>Subresource Integrity</strong> (SRI). This feature allows to check file checksums before they are run by the browser and therefore protects the original website if files have been modified, potentially by a malicious party.

SRI can be implemented by including the `integrity="..."` attribute in `<link>` and `<script>` elements, e.g.:

```
<script src="https://code.jquery.com/jquery-3.1.1.min.js" integrity="sha384-3ceskX3iaEnIogmQchP8opvBy3Mi7Ce34nWjpBIwVTHfGYWQS9jwHDVRnpKKHJg7" crossorigin="anonymous"></script>
```

You can generate SRI checksums (hashes) on <a href="https://www.srihash.org/">srihash.org</a>. Each time the file content is changed, the corresponding checksum needs to be updated as well for browsers to load it correctly.

<a href="https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity">Learn more &rarr;</a>

# Verifying & monitoring

- Most modern browsers will display detailed warnings in the webmaster tools' Console when mixed content is detected.
- Your websites can be checked using external tools:
  - <a href="https://observatory.mozilla.org/">observatory.mozilla.org</a>
  - <a href="https://securityheaders.io/">securityheaders.io</a>
  - <a href="https://www.ssllabs.com/ssltest/">ssllabs.com/ssltest/</a>

- <a href="https://developer.mozilla.org/en-US/docs/Web/Security/CSP/Using_CSP_violation_reports">CSP violation reports</a> can be used with <a href="https://report-uri.io/">report-uri.io</a> to log all events breaking the rules set by the Content Security Policy header, such as attempts to load insecure content.

We offer support and validation of HTTPS setups on the <a href="https://community.mybb.com/forum-179.html">Community forums</a>.
