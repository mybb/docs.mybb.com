---
layout: page
title:  "Login Problems"
categories: [faq]
---

# Unable to Log In

Most of the time this is a problem with your cookie settings being incorrect or inadequate. For more information about MyBB's cookies, read [Cookies](/1.8/development/cookies/).

Your cookie settings can be found in: **Admin CP** > **Configuration** > **Settings** > **General Configuration**. The two settings are *Cookie Domain* and *Cookie Path*.

By default, MyBB suggests Cookie Domain to be blank, and Cookie Path to be **/**. Although this theoretically will work, in many cases it is inadequate.

First a few examples of what your cookie settings should look like:

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

Alternatively you can use [this tool](http://www.dennistt.net/mybb/cookiesettings.php) to provide your cookie settings based on your forum's URL.

These cookie settings should work on all MyBB installations. If you have site-integration, your cookie settings may need to be more generalized.

After you change your cookie settings, please advise your users to log out and clear cookies stored by their browser, so that the new cookies can take effect.
