Postfix can be locked down to only accept email from the MailRoute servers.  Because of the wide range of possibilities for postfix configuration, please consider this a general guide, and not a hard-and-fast set of instructions.  


1. Edit your **main.cf** file.  This is usually found in **/etc/postfix/main.cf**
2. Add **199.89.0.0/21** to **mynetworks**
3. Set **smtpd_client_restrictions = permit_my_networks, reject**
4. Execute **postfix reload** to reload the settings and have them take effect right away


Please feel free to contact us at [support@mailroute.net][1] if you have any questions. We use postfix ourselves, and we'll do whatever we can to help.

   [1]: mailto:support@mailroute.net
