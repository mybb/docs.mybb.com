---
layout: page
title:  "Login Problems"
categories: [faq]
description: "Resolve issues with logging in to your forum."

redirect_from:
- /Help-Cannot_login.html
---

# Unable to Log In

Most of the time this is a problem with your cookie settings being incorrect or inadequate. For more information about MyBB's cookies, read [Cookies](/1.8/development/cookies/).

Your cookie settings can be found in: **Admin CP** > **Configuration** > **Settings** > **Site Details**. The two settings are *Cookie Domain* and *Cookie Path*.

By default, MyBB suggests Cookie Domain to be blank, and Cookie Path to be **/**. Although this theoretically will work, in many cases it is inadequate.

You can use [this tool](/tools/cookie-settings) to generate appropriate cookie settings, but here are some examples of what valid cookie settings look like:

<table>
	<tr>
		<th>Forum URL</th>
		<th>Cookie Domain</th>
		<th>Cookie Path</th>
	</tr>

	<tr>
		<td>http://www.example.com</td>
		<td>.example.com</td>
		<td>/</td>
	</tr>

	<tr>
		<td>http://www.example.com/directory/</td>
		<td>.example.com</td>
		<td>/directory/</td>
	</tr>

	<tr>
		<td>http://www.subdomain.example.com</td>
		<td>subdomain.example.com</td>
		<td>/</td>
	</tr>

	<tr>
		<td>http://www.subdomain.example.com/directory/</td>
		<td>subdomain.example.com</td>
		<td>/directory/</td>
	</tr>
</table>

These cookie settings should work on all MyBB installations. If you have site-integration, your cookie settings may need to be more generalized.

After you change your cookie settings, please advise your users to log out and clear cookies stored by their browser, so that the new cookies can take effect.
