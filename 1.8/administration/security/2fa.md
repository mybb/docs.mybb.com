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
		<td><a href="https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2"><img src="/assets/images/1.8/google-play-badge.png" alt="Get Google Authenticator on Google Play" /></a></td>
		<td><a href="https://itunes.apple.com/us/app/google-authenticator/id388497605?mt=8" target="itunes_store"><img src="/assets/images/1.8/app-store.png" alt="Download on the App Store" /></a></td>
		<td>-</td>
	</tr>
	<tr>
		<th>Authy</th>
		<td><a href="https://play.google.com/store/apps/details?id=com.authy.authy"><img src="/assets/images/1.8/google-play-badge.png" alt="Get Authy on Google Play" /></a></td>
		<td><a href="https://itunes.apple.com/us/app/authy/id494168017?mt=8&uo=4" target="itunes_store"><img src="/assets/images/1.8/app-store.png" alt="Download on the App Store" /></a></td>
		<td>-</td>
	</tr>
	<tr>
		<th>Microsoft Authenticator</th>
		<td>-</td>
		<td>-</td>
		<td><a href="https://www.microsoft.com/en-us/store/apps/authenticator/9wzdncrfj3rj"><img src="/assets/images/1.8/windows-store.png" style="width:150px;" alt="Windows Store" /></a></td>
	</tr>
</table>

# Setup and Configuration

1. Log into the MyBB Admin Control Panel, then navigate to the `Preferences` page of the `Home` tab.
2. An option, titled `Two-Factor Authentication` will be available. Check the box.
3. Click `Save Personal Notes & Preferences`.
4. A QR code will be presented to you when the page reloads. Scan that QR code with your authenticator app, and then the required setup is complete.

**If you lose your device or authenticator app**, make sure to save your backup codes in a safe place. They can be used if you no longer have the authenticator app for any reason. Note that the **codes are regenerated every time the backup codes page is viewed**, so you can only view them once. Viewing the page again will invalidate all old codes and generate a new set. As a result, it is strongly recommended to keep your backup codes in a safe place!

**NOTE:** This feature is only available to administrators' accounts via the admin cp. However, it is planned to extend this feature to others users with MyBB 2.0.

# Troubleshooting

- Verify that the server and authenticator device are in the same timezone. The codes are dependent upon time, within a 30 second time span.
