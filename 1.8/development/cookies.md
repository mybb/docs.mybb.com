---
layout: page
title:  "Cookies"
categories: [development]
---

## Introduction

[Cookies](https://en.wikipedia.org/wiki/HTTP_cookie) are important in MyBB to identify and verify logged-in users, and store inline-moderation selections. Incorrect cookie settings are the leading cause of login/logout problems on forums. If you or your users are having problems logging into the Front End of your board, see if the cookie settings are the culprit before posting your support request on the forum.

## MyBB Cookie Settings

MyBB has three inherent settings related to cookies:

- Cookie Domain
- Cookie Path
- Cookie Prefix

### Cookie Domain

This is the domain or subdomain that contains your forum. Usually a period/dot (".") is placed in front of this domain/subdomain in order to include all of its subdomains

### Cookie Path

This is the path from the root of your domain to your forum directory. The starting slash and ending slash should be included.

### Cookie Prefix

This is a prefix to all cookies used by your forum, to further prevent any conflicts with other installations of MyBB on the same domain or conflicts with other softwares.

### Examples

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

[This tool](/tools/cookie-settings) can help generate valid cookie settings.

## The Cookie List

The following is a list of the cookies that MyBB sets, and a note about each one:

<dl>
	<dt>acploginattempts</dt>
	<dd>Stores the number of ACP login attempts a user has had.</dd>

	<dt>acp_view</dt>
	<dd>Stores the admin's preferred view when inline editing users in the ACP.</dd>

	<dt>adminsid</dt>
	<dd>Stores the current admin's Admin Session ID.</dd>

	<dt>collapsed</dt>
	<dd>This cookie keeps track of which categories and boxes have been collapsed (as opposed to being expanded by default).</dd>

	<dt>coppadob</dt>
	<dd>Stores user date of birth to submit with registration.</dd>

	<dt>coppauser</dt>
	<dd>Stores whether the user is a COPPA user or not.</dd>

	<dt>failedlogin</dt>
	<dd>If the user has exceed the maximum login attempts, failedlogin stores the time (UNIX timestamp) of the failure.</dd>

	<dt>forumpass[$fid]</dt>
	<dd>Stores a version of the forum password for $fid when a user has entered it correctly, to avoid prompting the user for a password more often than required.</dd>

	<dt>inlinemod_</dt>
	<dd>
		There are multiple kinds of inline moderating cookies: forum, thread, and user, including:

		<ul>
			<li>inlinemod_forumfid</li>
			<li>inlinemod_threadtid</li>
			<li>inlinemod_useracp - for storing users to inline-edit in the Admin CP</li>
		</ul>

		fid is replaced with the forum ID and tid is replaced with the thread ID.

		The contents are a pipe-delimited and pipe-enclosed list of thread IDs or post IDs which have been checked for inline moderation.
	</dd>

	<dt>loginattempts</dt>
	<dd>Stores the number of login attempts a user has had.</dd>

	<dt>multiquote</dt>
	<dd></dd>

	<dt>mybb</dt>
	<dd>The mybb cookie is actually an array of cookies:</dd>

	<dt>mybb[announcements]</dt>
	<dd>Stores read annoucement IDs.</dd>

	<dt>mybb[forumread]</dt>
	<dd>Stores forums the user has read.</dd>

	<dt>mybb[lastvisit]</dt>
	<dd>This cookie stores the last time of visit in the UNIX timestamp format.</dd>

	<dt>mybb[lastactive]</dt>
	<dd>This cookie stores the last time that a forum page has been loaded, in the UNIX timestamp format.</dd>

	<dt>mybb[threadread]</dt>
	<dd>Stores threads read by the user.</dd>

	<dt>mybb[readallforums]</dt>
	<dd>Stores if the user has read all forums. Updated with mybb[lastvisit] in inc/functions_indicators.php.</dd>

	<dt>mybb[referrer]</dt>
	<dd></dd>

	<dt>mybblang</dt>
	<dd>Stores the language preference of a guest.</dd>

	<dt>mybbratethread[{$tid}]</dt>
	<dd>Stores the user's rating of thread $tid.</dd>

	<dt>mybbtheme</dt>
	<dd>Stores the theme preference of a guest.</dd>

	<dt>mybbuser</dt>
	<dd>This cookie stores the login information for the Front End, and is set when a user logs in, and is removed when the user logs out. The UID and the login key are stored in this cookie.</dd>

	<dt>pollvotes[$pid]</dt>
	<dd>Stores a guest's vote on poll $pid.</dd>

	<dt>sid</dt>
	<dd>The current user's Session ID.</dd>
</dl>
