---
layout: page
title:  "Warning System"
---

# Warning System

The MyBB Warning System allows for easy warning of users for various offenses, and allows for automatic punishments to be given based on the warning level. There are various board settings regarding the warning system. Also, there is a section in the Admin CP for configuration of the warning system - including both warning types and warning levels (actions that occur at a certain percentage).

If enabled in the board settings in the Admin CP, a user will be able to see their warning level in their profile and will be able to view their recent warnings from their User CP. More information on the warning log in the User CP can be found in the [User CP article](/usage/user-cp).

## Warning a User

### Warn a User

You can either warn a user from their profile or from a post of theirs. To warn a user from their profile, go to the user's profile and next to **Warning Level** select **Warn**. To warn a user from a post of theirs, click on the **Warn** button at the far right of the options bar. Both of these take you to the warning page; however, if you warn a user from a post of theirs, the post will be included in the **Warning Log**.

On the page, you will see the following:

![Warning panel screen](/assets/images/mod-cp/warning-system-warn-user.jpg)

**Username**

The username of the user you are warning, and a link to their profile. 

**Post**

If you are warning a user from a post of theirs, a link to the post will be shown, with the title of the post. 

**Administrative Notes** 

Here you can enter notes regarding why this user was warned, only for users who can warn other users to see. 

**Warning Type** 

The type or reason for warning this user. The user will see this field. This can either be one of the administrative-set warning types or a custom reason. Each warning type also lists the number of points that will be added to the user's warning level. When selecting an administrative-set warning type, the user's new warning level will be displayed, and any actions that will result of the warning will be listed (warning levels). If you select to enter a custom reason, you must enter in the reason, the number of points to be awarded, and when the warning will expire, choosing either a number of hours, days, weeks, months, or never. 

**Notify User**

If you wish to send the user a private message alongside with the warning, select the checkbox **Send this user a private message notifying them of this warning**. A form will be loaded allowing you to enter in a subject for the private message and a message. A MyCode editor is shown for the message, and the smilies are also shown to the left. 

Select **Warn User** to add the warning and to, if chosen, send the private message to the user.

**Warning Log**

![Warning log screen](/assets/images/mod-cp/warning-system-warn-log.jpg)

From the user's postbit and profile, you will see the user's warning level. Clicking on this takes you a page listing all of their warnings (the user's warning log). Warnings can either be active or expired (they are separated in this listing). For each warning, you see the warning type/reason, the post the user was warned for (if applicable), the date issued, when the warning will expire (if ever, and if it has not already expired), who issued the warning, and will be given a link to view more information on the warning.

Warning Details

![Warning details screen](/assets/images/mod-cp/warning-system-warn-details.jpg)

Clicking on *View* for a warning from the warning log takes you to a page that lists all of the information about the warning. This includes:

**Username**

The name of the user who was warned 

**Warning** 

The warning type / reason, and the number of points the warning was worth 

**Date Issued** 

The date and time the warning was issued 

**Issued By**

The user who warned this user 

**Expires** 

The date and time the warning will expire. If the warning has already expired, you will be told so, and will be shown the date and time the warning expired in parentheses.

**Administrative Notes** 

These are the notes the warner added when warning the user, to not be displayed to the warned user. 

### Revoke this Warning

You may also opt to revoke the warning, which will essentially expire the warning early, making it no longer count toward the user's warning level. However, this will not remove any bans or suspensions that were imposed as a result of the warning.

To revoke the warning, you must enter in a reason. The reason should explain why the warning is being revoked early.

There is no way to permanently remove all traces of a warning from the front end of the forum. After a user has been warned, the warning will remain on record, regardless of whether or not it counts towards the user's warning level.
The warning has been revoked

If the warning has been revoked, a separate table will be displayed saying so. This will include the following information:

**Revoked by** 

The user who revoked the warning
    
**Date Revoked** 

The date and time the warning was revoked 
    
**Reason** 

The reason entered at the time the warning was revoked by the user who revoked the warning. 
