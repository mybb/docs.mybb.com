---
layout: page
title:  "Spam"
categories: [administration]
---
Without proper protections enabled, forums inevitably get targeted by spammers. Fortunately, MyBB has several built-in features that help protect your community from spammers.

# Automated vs Human Spammers

When receiving an influx of spam, it's important to identify if you're up against automated (software) "spambots" or human spammers. Human spammers are often able to get past security questions, captchas, and most other antispam "challenges." If human spammers are the culprit in an attack mounted against your forum, much different steps must be taken to reduce the amount of spam that gets through to public view.

Note that Automated Spammer countermeasures can still be useful against human spammers, but are often just not as effective.

## Automated Spammer Prevention

The following are a set of steps that often help prevent spam from automated spammers.

### Registration Security Questions

Since the release of MyBB 1.8, Security Questions have been in the core of MyBB. Inspired by -G33K-'s [1.6 Registration Security Question](https://mods.mybb.com/view/registration-security-question) plugin, this feature allows you to configure questions that a visitor may have to answer when registering in your community. To configure the Security Questions, go to `Admin CP > Configuration > Security Questions`.

When registering, the visitor is given one random question, and the ability to "Refresh" and get a new question. For this reason, it's important to make sure that all of your questions are high-quality and hard for an automated system to figure out the answer to. For example, the default "What does 2 + 2 equal?" question is *not* hard because most automated systems have figured out how to solve math problems. Ideally, questions should be something that only someone who has knowledge in the subject matter of your community would know. For a tech forum, this might mean a question like "What is the SKU designator for an Intel Mobile CPU?" The answer to this would be "M" or "m."

After adding several questions, monitor the Correct/Incorrect rate of each question. An Incorrect rate that is disproportionately high compared to the Correct rate might indicate that the question is too difficult and preventing legitimate users from registering.

### Minimum Registration Time

Another useful feature to prevent bot signups is the "Minimum Registration Time" setting, located in `Admin CP > Configuration > Login and Registration Options`. This ensures that the time to fill out the registration form is similar to the time it would take for a human to complete it. Automated systems want to instantly fill out the form and submit it to maximize their efficiency across the Internet, and so this feature will stop automated registrations that behave in that way.

The default setting value is 15 seconds, which is often at least how long it takes for humans to fill out the registration form.

### Hidden CAPTCHA

In `Admin CP > Configuration > Login and Registration Options`, a "Hidden CAPTCHA" can be configured. This is a text field hidden to normal visitors who have JavaScript enabled in their browser. However, automated systems will try to intelligently fill the field with something. If the field is filled, registration is denied.

### CAPTCHA Images for Registration & Posting

In `Admin CP > Configuration > General Configuration`, a visual CAPTCHA challenge can be configured from a variety of options.

+ **No CAPTCHA**, in which the visual CAPTCHA challenge is disabled. This is not recommended, as disabling the CAPTCHA Images makes it much easier for automated systems to post spam.
+ **MyBB Default CAPTCHA**, in which a PHP GD captcha is generated. This can often be passed by automated systems and usually should not be used.
+ **reCAPTCHA**, which displays a "ReCAPTCHA" challenge; signup is required at [Google's ReCAPTCHA site](https://www.google.com/recaptcha/intro/index.html) to get the Public and Private keys that must be configured.
+ **NoCAPTCHA reCAPTCHA**, which displays the latest version of reCAPTCHA, in which a user simply clicks a checkbox to continue, or as a fallback must complete a simple picture-selection challenge; signup is required at [Google's ReCAPTCHA site](https://www.google.com/recaptcha/intro/index.html to get the Public and Private keys that must be configured.

### Stop Forum Spam

In `Admin CP > Configuration > Stop Forum Spam`, you can configure all user registration information to be checked against [Stop Forum Spam's database](https://stopforumspam.com/) of known spammers, which crowdsources data from many websites. If the information that a registering user just entered is in their database, registration will be denied to them. Registration is required at their [official forum](https://www.stopforumspam.com/forum/register.php) to get an API key.

## Human Spammers

Spam by cheaply-paid humans is becoming increasingly common, and this method unfortunately defeats almost all of the antispam measures above, because an actual human can solve all of the challenges and will register much like a normal person. Fortunately, there are still ways to minimize the damage they can do; unfortunately, more manual effort may be required.

### Moderate First Posts

Moderating a user's first post is a semi-intrusive but surefire way to stop spammers in your community. Even if a human spammer gets past the registration, their first post (and any until the first is approved) will go into the moderation queue, where a moderator can verify the content of the post to see if it looks like spam. Ad Bakker of the MyBB Community Forums created a [plugin for 1.8](https://community.mybb.com/thread-173075-post-1171321.html#pid1171321) that can be used to perform this action. Alternatively, the Group Promotions feature of MyBB can be leveraged to do something very similar without the plugin.

# If a Spammer Gets Through, Purge Them!

Sometimes, despite relentless efforts, spammers will get through your countermeasures. If they haven't posted too much yet, the Purge Spammer feature (inspired by [MattRogowski's Goodbye Spammer for 1.6](https://mods.mybb.com/view/goodbye-spammer)) makes it easy to instantly undo the damage that has been done. Just go to one of the spammer's posts, and click the **Purge Spammer** button in the postbit, and all of their content (posts, threads, PMs, signature, website, etc.) will be deleted and the entire user can be either deleted or banned. These settings can be configured in `Admin CP > Configuration > Purge Spammer`.
