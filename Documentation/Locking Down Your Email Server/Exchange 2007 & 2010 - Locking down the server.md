Microsoft Exchange 2007 can be locked down to only accept email from the MailRoute servers by following these steps:

1.  Open **Exchange Management Console**
2.  Under the **Server Configuration** node, select **Hub Transport**
3.  Choose the receive connector you are using for your incoming SMTP traffic, right click and select **Properties**
4.  Click the **Network** tab
5.  Find where it says **Receive mail from remote servers which have these IP addresses**
6.  Select **Add -> IP Address**
7.  In the **Add IP address(es) of Remote Servers** box, enter the MailRoute network in CIDR notation:

        199.89.0.0/21

8.  There is probably a default entry in there for an address range that will need to be removed, because it allows connection from any IP address.  It looks like this:
    
        0.0.0.0 - 255.255.255.255

    These changes should take effect right away without having to restart any services, but we have seen some instances where a restart of Exchange services is required.

Microsoft has online documentation on how to do this at http://technet.microsoft.com/en-us/library/bb691331(EXCHG.80).aspx

You may need to refer to other sections of that technical reference document if your Exchange configuration is non-standard.

