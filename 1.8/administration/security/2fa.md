---
layout: page
title:  "Using Two-Factor Authentication with MyBB"
categories: [security]
---

# Authenticator Apps

The following apps can be used as Two-Factor Authentication Apps. Note that this list is incomplete and that more apps exist for different operating systems.

<table>
	<tr>
		<th></th>
		<th>Android</th>
		<th>iOS</th>
		<th>Windows Phone</th>
	</tr>
	<tr>
		<th>Google Authenticator</th>
		<td><a href="https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2"><img alt="Android app on Google Play" src="https://developer.android.com/images/brand/en_app_rgb_wo_45.png" /></a></td>
		<td><a href="https://itunes.apple.com/us/app/google-authenticator/id388497605?mt=8" target="itunes_store"><img src="https://devimages.apple.com.edgekey.net/app-store/marketing/guidelines/images/badge-download-on-the-app-store.svg" alt="Download on the App Store" /></a></td>
		<td>-</td>
	</tr>
	<tr>
		<th>Authy</th>
		<td><a href="https://play.google.com/store/apps/details?id=com.authy.authy"><img alt="Android app on Google Play" src="https://developer.android.com/images/brand/en_app_rgb_wo_45.png" /></a></td>
		<td><a href="https://itunes.apple.com/us/app/authy/id494168017?mt=8&uo=4" target="itunes_store"><img src="https://devimages.apple.com.edgekey.net/app-store/marketing/guidelines/images/badge-download-on-the-app-store.svg" alt="Download on the App Store" /></a></td>
		<td>-</td>
	</tr>
	<tr>
		<th>Microsoft Authenticator</th>
		<td>-</td>
		<td>-</td>
		<td><a href="https://www.microsoft.com/en-us/store/apps/authenticator/9wzdncrfj3rj"><img src="/assets/images/1.8/windows-store.png" style="width:150px;" alt="Windows Store" /></a></td>
	</tr>
</table>

# Troubleshooting

+ Verify that the server and authenticator device are in the same timezone. The codes are dependent upon time, within a 30 second time span.
