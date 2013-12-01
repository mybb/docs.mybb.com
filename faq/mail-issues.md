---
layout: page
title:  "Mail Issues"
---

# Mail Issues

If you or your users are having problems with receiving mail from your server, please follow these steps before posting a support request so that we can more quickly pinpoint the problem.

First please check that the mail has not been sent into the junk/spam mail folder.

MyBB relies on the [PHP Mail function](http://php.net/manual/en/function.mail.php) to send its mail. Thus, it is important that the PHP mail function is working.

**Test script:**

Please create a new `.php` file with this content:

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
       } 
    ?>
  
Replace *your.email@address.com* with your email address. Upload this file to your webserver and run it with your browser.

It should say **Mail was sent by PHP** and there should not be any other errors that show up.

Some webhosts have various restrictions on PHP mail. Some hosts require that the **From** address be a mailbox address on their server. Other hosts may disable the mail function completely. Please ask your webhost if there are any special restrictions they have on sending mail via PHP.

If your webhost has restricted that only mails from there own domain is allowed, try to edit the file `inc/functions.php`. Look for:

    mail($to, $subject, $message, $headers);
    
and include above: 

    ini_set("sendmail_from", " forum@YOURDOMAIN.com "); 
    
Then it should look like this:

    ini_set("sendmail_from", " forum@YOURDOMAIN.com "); 
    mail($to, $subject, $message, $headers);
    
*YOURDOMAIN* must be replaced by the domain where the forum is hosted.
