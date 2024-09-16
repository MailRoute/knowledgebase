---
created_at: 2021-02-23 17:54:26
date: 2024-04-12 14:40:30
description: Detailed list of SMTP response codes for the Postfix email server, with
  explanations. Covers positive completion, transient negative, and permanent negative
  replies. Useful for email administrators and troubleshooting.
draft: true
params:
  author: Unknown
summary: The article provides a comprehensive list of SMTP response codes used by
  the Postfix email server software, along with brief explanations of each code. The
  codes cover various scenarios, including successful message delivery, temporary
  errors, and permanent failures.
tags: null
title: Postfix SMTP Response Errors
---


Here's a list of SMTP Response Codes for the wonderful email server software
Postfix (http://postfix.org).

MailRoute uses postfix, along with countless other email providers and
administrators. We're providing a list of possible response codes you may see
from our servers, or in our relay to other postfix servers.

Fortunately, postfix error codes are pretty self-explanatory. If you're
confused about one that you see, please let us know at support@mailroute.net
and we are happy to try to explain it further.

Response codes are in the form of xyz

Positive Completion Codes - these mean that all is well, and that the server
accepted the client's request. These are all pretty self-explanatory.

220 2.0.0 Ready to start TLS

221 2.0.0 Bye

235 2.7.0 Authentication successful

250 2.0.0 Ok

250 2.0.0 Ok: NNN bytes queued as <queue-id>

250 2.0.0 Ok: queued as <queue_id>

250 2.1.0 Ok

250 2.1.5 Ok

Transient Negative Completion Replies - these codes indicate that there was an
error, but that the client should retry again later.

421 4.3.0 Server local data error

421 4.3.0 Server local error

421 4.3.2 All screening ports are busy

421 4.3.2 All server ports are busy

421 4.3.2 No system resources

421 4.3.5 Server configuration error

421 4.4.2 Error: timeout exceeded

421 4.7.0 Error: too many connections from <detail>

421 4.7.0 Error: too many errors

421 4.7.0 Error: too many new TLS sessions from <detail>

421 4.7.0 Error: too many connections

421 4.7.0 Server closing connection

444 4.3.2 <foobar>: Helo command rejected: Try again later

450 4.1.2 <rname@nxdomain.porcupine.org>: Recipient address rejected: Domain
not found

450 4.1.8 <foo@bad.domain>: Sender address rejected: Domain not found

450 4.1.8 <sname@nxdomain.porcupine.org>: Sender address rejected: Domain not
found

450 4.1.8 <user@nxdomain.porcupine.org>: Sender address rejected: Domain not
found

450 4.1.8 <user@xn--1xa.porcupine.org>: Sender address rejected: Domain not
found

450 4.3.0 Error: command failed

450 4.7.1 <123.123.123.123|dunno.com>: Helo command rejected: Host not found

450 4.7.1 Client host rejected: cannot find your hostname, [1.1.1.1]

450 4.7.1 Error: too many AUTH commands from <detail>

450 4.7.1 Error: too many recipients from <detail>

450 4.7.1 Error: too much mail from <detail>

451 4.3.0 <reject@dunno.domain>: Temporary lookup failure

451 4.3.0 Queue file write error

451 4.3.0 Temporary lookup error

451 4.3.5 <>: Sender address rejected: Server configuration error

451 4.3.5 <foo.dunno.com[131.155.210.17]>: Client host rejected: Server
configuration error

451 4.3.5 <foobar>: Helo command rejected: Server configuration error

451 4.3.5 <reject@dunno.domain>: Recipient address rejected: Server
configuration error

451 4.3.5 <reject@dunno.domain>: Sender address rejected: Server configuration
error

451 4.3.5 Server configuration error

451 4.3.5 Server configuration problem

451 4.7.1 Service unavailable - try again later

452 4.5.3 Error: too many recipients

454 4.3.0 Try again later

454 4.7.0 Error: too many new TLS sessions from <detail>

454 4.7.0 Temporary authentication failure: <detail>

454 4.7.0 TLS not available due to local problem

Permanent Negative Completion Replies - if the postfix server sends one of
these errors, the client should not retry, and should probably send back a DSN
("Delivery Status Notification") to the original sender, and include the error
message.

500 5.3.0 Error: command failed

500 5.5.2 Error: bad syntax

500 5.5.2 Error: bad UTF-8 syntax

500 5.5.6 SASL response limit exceeded

501 5.1.3 Bad recipient address syntax

501 5.1.7 Bad sender address syntax

501 5.5.2 <.1.2.3.4>: Helo command rejected: invalid ip address

501 5.5.4 Bad <smtp command> attribute name: <detail>

501 5.5.4 Bad ENVID parameter syntax

501 5.5.4 Bad message size syntax

501 5.5.4 Bad RET parameter syntax

501 5.5.4 Error: attribute value too long

501 5.5.4 Error: attribute=value expected

501 5.5.4 Error: Bad NOTIFY parameter syntax

501 5.5.4 Error: Bad ORCPT parameter syntax

501 5.5.4 Syntax: AUTH mechanism

501 5.5.4 Syntax: BDAT count [LAST]

501 5.5.4 Syntax: DATA

501 5.5.4 Syntax: MAIL FROM:<address>

501 5.5.4 Syntax: NOOP

501 5.5.4 Syntax: RCPT TO:<address>

501 5.5.4 Syntax: RSET

501 5.5.4 Syntax: STARTTLS

501 5.5.4 Syntax: VRFY address

501 5.7.0 Authentication aborted

501 5.7.1 DSN support is disabled

502 5.5.1 Error: command not implemented

502 5.5.1 VRFY command is disabled

502 5.5.2 Error: command not recognized

503 5.5.1 Error: already authenticated

503 5.5.1 Error: authentication not enabled

503 5.5.1 Error: DATA after BDAT

503 5.5.1 Error: MAIL after BDAT

503 5.5.1 Error: MAIL transaction in progress

503 5.5.1 Error: need MAIL command

503 5.5.1 Error: need RCPT command

503 5.5.1 Error: nested MAIL command

503 5.5.1 Error: RCPT after BDAT

503 5.5.1 Error: send HELO/EHLO first

503 5.5.4 Error: multiple AUTH= options

503 5.5.4 Error: send AUTH command first

503 5.7.0 Error: access denied for foo@example.com

504 5.5.2 <foo@foo>: Recipient address rejected: need fully-qualified address

504 5.5.2 <foo@foo>: Sender address rejected: need fully-qualified address

504 5.5.2 <foo>: Helo command rejected: need fully-qualified hostname

504 5.5.2 <foo>: Recipient address rejected: need fully-qualified address

504 5.5.2 <foo>: Sender address rejected: need fully-qualified address

504 5.5.4 Encryption required for requested authentication mechanism

521 5.3.2 Service currently unavailable

521 5.5.1 Error: command not implemented

521 5.5.1 Protocol error

521 5.5.4 Syntax: BDAT count [LAST]

521 5.7.0 Error: I can break rules, too. Goodbye.

530 5.7.0 Must issue a STARTTLS command first

535 5.7.8 Error: authentication failed: <detail>

550 5.1.0 <baz@example.com>: Sender address rejected: User unknown in local
recipient table

550 5.1.1 <foo@example.com>: Recipient address rejected: User unknown in local
recipient table

550 5.3.2 Service currently unavailable

550 5.5.0 Service unavailable

550 5.5.1 Protocol error

550 5.7.0 Error: insufficient authorization

550 5.7.1 <>: Sender address rejected: Go away postmaster

550 5.7.1 Client host rejected: cannot find your hostname, [1.1.1.1]

550 5.7.27 <sname@nullmx.porcupine.org>: Sender address rejected: Domain
nullmx.porcupine.org does not accept mail

551 5.7.1 Null BDAT request

552 5.3.4 Chunk exceeds message size limit

552 5.3.4 Message file too big

552 5.3.4 Message size exceeds file system imposed limit

553 5.6.7 Must declare SMTPUTF8 to send unicode address

554 5.0.0 <1.2.3.4>: Client host rejected: reject

554 5.0.0 <1.2.3.4>: Helo command rejected: reject

554 5.1.0 <user@dunno.com>: Sender address rejected: reject

554 5.1.2 <user@dunno.com>: Recipient address rejected: Domain not found

554 5.1.1 <user@dunno.com>: Recipient address rejected: reject

554 5.1.2 <user@dunno.com>: Recipient address rejected: reject

554 5.1.3 <user@dunno.com>: Recipient address rejected: reject

554 5.1.4 <user@dunno.com>: Recipient address rejected: reject

554 5.1.5 <user@dunno.com>: Recipient address rejected: reject

554 5.1.6 <user@dunno.com>: Recipient address rejected: reject

554 5.1.7 <user@dunno.com>: Sender address rejected: reject

554 5.1.8 <user@dunno.com>: Sender address rejected: reject

554 5.1.8 <user@no.sender.domain>: Sender address rejected: Domain not found

554 5.4.0 <1.2.3.4]>: Client host rejected: reject

554 5.4.0 <1.2.3.4>: Helo command rejected: reject

554 5.4.0 <uesr@dunno.com>: Recipient address rejected: reject

554 5.4.0 <uesr@dunno.com>: Sender address rejected: reject

554 5.5.1 Error: need RCPT command

554 5.5.1 Error: no valid recipients

554 5.5.1 Error: TLS already active

554 5.5.1 Error: TLS already active\r\n))

554 5.7.1 <1.2.3.4>: Client host rejected: match 1.2.3

554 5.7.1 <anyone@reject.domain>: Recipient address rejected: Access denied

554 5.7.1 <anyone@reject.domain>: Sender address rejected: Access denied

554 5.7.1 <bad-sender@any.domain>: Sender address rejected: match bad-sender@

554 5.7.1 <bad.domain>: Helo command rejected: match bad.domain

554 5.7.1 <bar.duno.com[44.33.22.11]>: Client host rejected: Access denied

554 5.7.1 <foo.dunno.com>: Helo command rejected: Access denied

554 5.7.1 <foo@ibm.com>: Recipient address rejected: Relay access denied

554 5.7.1 <random.bad.domain[123.123.123.123]>: Client host rejected: match
bad.domain

554 5.7.1 <reject@this.address>: Sender address rejected: match
reject@this.address

554 5.7.1 <rejecttext@bad.domain>: Sender address rejected: text

554 5.7.1 <rname@rdomain>: Relay access denied

554 5.7.1 <sname@spike.porcupine.org>: Sender address rejected: ns or mx
server spike.porcupine.org

554 5.7.1 <spike.porcupine.org>: Helo command rejected: name server
spike.porcupine.org

554 5.7.1 <spike.porcupine.org>: Helo command rejected: ns or mx server
spike.porcupine.org

554 5.7.1 <rname@rdomain>: Relay access denied

554 5.7.1 <rname@rdomain>: Relay access denied

554 5.7.1 <rname@rdomain>: Relay access denied

554 5.7.1 Service unavailable; Client host [127.0.0.2] blocked using
<blacklist>

556 5.1.10 <rname@nullmx.porcupine.org>: Recipient address rejected: Domain
nullmx.porcupine.org does not accept mail

