---
layout: page
title:  "Banning"
categories: [administration]
---

The MyBB Admin CP Banning page, found under the "Configuration" tab, offers the ability to ban IP Addresses and disallow usernames and email addresses. Wildcard support is included for IP addresses, usernames, and email addresses, and for all you can view the date banned and the last attempted use. More information for each sub-page is found below.

## Banned IPs

Banned IP addresses disallow access for anyone accessing your MyBB forum from the IP addresses banned. Also supported is banning ranges of IP addresses, using * to represent the wildcard. You can view when each IP address was banned, and when the IP address last attempted to access the forum.

#### Banning IPs

To ban an IP address, just enter the IP address, or range of IP addresses using an asterisk (*) to represent the wildcard, into the form at the bottom of the page and select "Ban IP Address."

#### Removing IP Bans

You can later delete any banned IP address by simply selecting the delete icon on the right hand side of the page for the corresponding IP address.

## Banned Accounts

The banning section is located under the Users & Groups tab and it allows you to ban registered users.

#### Banning Accounts

To ban a registered user, you need to fill out the following fields:

[*] **Username** - The username of the account you wish to ban. Auto-complete is enabled on this field. (This field is necessary).
[*] **Ban reason** - The reason to show the user explaining why they were banned.
[*] **Ban Length** - The length of the ban (and when it will be lifted). (This field is necessary).

#### Editing or Removing a Ban for an Account

You can remove a ban for a user by selecting the **Lift** option under the *Controls* section. Also, you can edit the ban reason or expand the ban by selecting the **Edit** option under the *Controls* section.

#### Pruning Threads & Posts

You can prune (delete) all threads and posts by a specific user by selecting the **Prune Threads & Posts** under the *Moderation* section.

## Disallowed Usernames

Disallowing usernames allows you to prevent usernames from being registered by users. From the Admin CP, you can view the date the username was disallowed as well as its last attempted use. It is important to note that disallowing a username does not affect already registered users, and does not remove any access for existing users; it only disallows the username for new registrations.

#### Disallowing Usernames

To ban a username, simply fill in the desired username to be banned in the form and select "Disallow Username." Be aware that partial matches are disallowed, so any username containing the disallowed username will not be able to be registered.

#### Removing Disallowed Usernames

You can later delete any disallowed usernames by simply selecting the delete icon on the right hand side of the page for the corresponding username.

## Disallowed Email Addresses

Disallowing email addresses allows you to prevent specific email addresses, or email address domains to be used by users. You can view the date the email address was disallowed and the last attempted use, as well. You can simply ban entire domains without using the wildcard feature; simply enter the domain when disallowing the email address rather than a full email address. It is not necessary to enter **\*@bannedomain.com** - you can enter just **bannedomain.com**

**Please note:** If you would like to have any email addresses that you disallow through the Admin CP to no longer be used by existing users, you must set "Users Keep Email" under "Login and Registration Options" to No.

#### Disallowing Email Addresses

To ban an email address or email address domain, simply fill in the desired email address or domain to be banned in the form and select "Disallow Email Address."

#### Removing Disallowed Email Addresses

You can later delete any disallowed email addresses by simply selecting the delete icon on the right hand side of the page for the corresponding email address.
