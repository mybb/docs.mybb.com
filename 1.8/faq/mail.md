---
layout: page
title:  "Mail Issues"
categories: [faq]
description: "Resolve issues with receiving mail sent from your forum."

redirect_from:
- /Help-Mail.html
---

# Mail Issues

If you or your users are having problems receiving mail from your forum, please follow these steps before posting a support request so that we can more quickly pinpoint the problem.

First, check that the mail has not been sent into the junk/spam mail folder. Mail could land in the junk folder due to a variety of reasons, such as your host's server being blacklisted for previous sendings of spam (usually by a bad customer).

## Testing PHP Mail

MyBB relies on the [PHP Mail function](https://secure.php.net/manual/en/function.mail.php) to send its mail. Thus, it is important that the PHP mail function is working.

**Test script:**

Create a new `.php` file with this content:

```php
    <?php
     error_reporting(E_ALL);
       $to = 'your.email@address.com';
       if(mail($to, 'Testing mail', 'This is a mailing test to see if PHP mail works.'))
       {
        echo 'Mail was sent by PHP';
       }
       else
       {
        echo 'PHP could not send the mail';
        print_r(error_get_last());
       }
    ?>
```

Replace `your.email@address.com` with your email address. Upload this file to your webserver and browse to it in order to run the test.

It should say `Mail was sent by PHP` and there should not be any errors displayed.

## Host Restrictions

Some webhosts place restrictions on PHP mail. For example, some require that the `From` address be an address configured on their server; other hosts may disable the PHP mail function completely.Check with your webhost if there are any restrictions in place for sending mail via PHP.

If your webhost only allows sites to send mail from their own domain, edit the file `inc/mailhandlers/php.php` to try a workaround fix.

Find:
```php
    if($mybb->safemode)
    {
        $sent = @mail($this->to, $this->subject, $this->message, trim($this->headers));
    }
    else
    {
        $sent = @mail($this->to, $this->subject, $this->message, trim($this->headers), $this->additional_parameters);
    }
```

Add before:
```php
    ini_set("sendmail_from", "forum@YOURDOMAIN.com");
```

The final result of the edit should be:
```php
    ini_set("sendmail_from", "forum@YOURDOMAIN.com");
    if($mybb->safemode)
    {
        $sent = @mail($this->to, $this->subject, $this->message, trim($this->headers));
    }
    else
    {
        $sent = @mail($this->to, $this->subject, $this->message, trim($this->headers), $this->additional_parameters);
    }
```

`YOURDOMAIN` in the above code must be replaced by the domain where the forum is hosted.
