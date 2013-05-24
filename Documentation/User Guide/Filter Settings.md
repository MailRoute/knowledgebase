## Filter Settings

If the domain administrator has provided us with a complete list of user accounts for your domain, then it enables per-user policy settings.  These override the domain-wide default settings your administrator has selected.

### Default Settings

You can set your account to use the domain-wide settings by choosing the checkbox **Use the default filter settings for my domain**

![Filter Settings - Use Default](http://static.mailroute.net/kb/filter_default.png)


### Spam Filter Settings

The Spam Filter settings has the most options.  You can choose from various pre-defined presets for filtering, or set your own, with any level of granularity.

Messages that are **spammy** can be delivered with their Subject lines rewritten.  **Spam** messages can be quarantined.  And you can choose the score at which each of those happens.  Our standard settings simply quarantines at a score of 7.0.  But you might want to make this number higher or smaller, or add the option to rewrite the Subject.  It's entirely in your control.

![Filter Settings - Spam](http://static.mailroute.net/kb/filter_spam.png)

### Virus Filter Settings

Your options for virus-infected emails are much simpler - do you want a notification sent to you when a virus-infected message is quarantined?

![Filter Settings - Virus](http://static.mailroute.net/kb/filter_virus.png)


### Size Filter Settings

Likewise, you can opt to reduce the maximum allowed message size for your email.  Our maximum limit is 150MB.

![Filter Settings - Size](http://static.mailroute.net/kb/filter_size.png)

### Banned Filetypes Filter Settings

Banned Filetypes are messages that contain various types of dangerous enclosures.  The standard filetypes blocked by this filter include: '.bat', '.cmd', '.com', '.cpl', '.dll', '.exe', '.pif', '.scr', and '.vbs'.

These restrictions apply to files embedded inside other files, like zip or tar files too.

Besides quarantining these emails and deciding if you want a notification, you can also allow them through to you.  You can even set a "plus extension" for delivery, so you can have the message delivered to a variant of your email address, like **user+banned@domain.com**  Some people like to use this to support client-side filtering.

![Filter Settings - Banned](http://static.mailroute.net/kb/filter_banned.png)

### Bad Header Filter Settings

The Bad Headers filter has the same options as those for the Banned Filetype filter.  Bad headers are messages that violate the internet-standard RFCs. The checks include verifying the MIME structure of an email message, checking for control characters (like NUL and CR), looking for improperly encoded 8-bit characters in an email header (per RFC 5322), and headers longer than the maximum allowed length of 998 characters (per RFC 2822)

Of all the things here, this is the one most likely to have a false positive, particularly with various mailing lists. You might want to just let it go ahead and deliver these messages. Or deliver it with an extension. Or if you do want to quarantine it, enable the notification.

![Filter Settings - BadHdr](http://static.mailroute.net/kb/filter_badhdr.png)

