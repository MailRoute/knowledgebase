---
created_at: 2018-05-23 20:27:38
date: 2022-12-15 13:34:14
description: Detailed overview of MailRoute's security, privacy, and system architecture,
  covering data segregation, processing controls, security policies, incident response,
  physical security, backups, disaster recovery, encryption, and data retention.
draft: true
params:
  author: Unknown
summary: The article outlines the security, privacy, and architectural details of
  MailRoute, Inc. and its affiliates, including data segregation, processing controls,
  security policies, incident management, physical security, backup and disaster recovery
  processes, data encryption, and data retention policies.
tags: 
- gdpr
title: GDPR - Security, Privacy and Architecture of MailRoute, Inc. and its Affiliates
---


# Security, Privacy and Architecture of MailRoute, Inc. and its Affiliates

### Published: May 15, 2018

### MR’s Corporate Trust Commitment

MR (as defined in the MailRoute Protection Addendum (the “Addendum”) is
committed to achieving and maintaining the trust of our Customers (as defined
in the Addendum). Integral to this mission is providing a robust security and
privacy program that carefully considers data protection matters across our
suite of services, including the email processing services we offer our
Customers (“Services”).

### Services Covered

This documentation describes the architecture of, the security- and privacy-
related audits and certifications received for, and the administrative,
technical and physical controls applicable to, the services branded as MR,
Inc.

### Architecture and Data Segregation

The Services are operated in a multitenant architecture that is designed to
segregate and restrict Customer Data, as defined in the Data Processing
Addendum, access based on business needs. The architecture provides an
effective logical data separation for different customers via customer-
specific "Customer IDs" and allows the use of customer and Customer role-based
access privileges. Additional data segregation is ensured by providing
separate environments for different functions, especially for testing and
production. The specific infrastructure used to host Customer Data is
described in the “Infrastructure and Sub-processors” documentation available
at <https://support.mailroute.net/hc/en-
us/articles/360001359847-Infrastructure-and-Sub-processors-for-MailRoute-Inc-
and-its-Affiliates>

### Control of Processing

MR has implemented procedures designed to ensure that Customer Data is
processed only as instructed by the customer, throughout the entire chain of
processing activities by MR and its sub- processors. In particular, MR and its
affiliates have entered into written agreements with their sub- processors
containing privacy, data protection and data security obligations that provide
a level of protection appropriate to their processing activities. Compliance
with such obligations as well as the technical and organizational data
security measures implemented by MR and its sub-processors are subject to
regular audits. The “Infrastructure and Sub-processors” documentation
describes the sub- processors and certain other entities material to MR’s
provision of the Services.

### Third-Party Functionality

Certain features of the Services use functionality provided by third parties,
including Billing and Customer Support functionality.

### Security Controls

The Services include a variety of configurable security controls that allow
customers to tailor the security of the Services for their own use. Please see
additional information on such controls in the Security Implementation Guide.

### Security Policies and Procedures

The Services are operated in accordance with the following policies and
procedures to enhance security:

  * Customer passwords are stored using a one-way salted hash. ID operated on, operation performed (created, updated, deleted) and source IP address. Note that source IP address might not be available if NAT (Network Address Translation) or PAT (Port Address Translation) is used by Customer or its ISP.
  * If there is suspicion of inappropriate access, MR can provide customers log entry records and/or analysis of such records to assist in forensic analysis when available. This service will be provided to customers on a time and materials basis.
  * Data center physical access logs, system infrastructure logs, and application logs will be kept for a minimum of 90 days. Logs will be kept in a secure area to prevent tampering.
  * Email processing logs are kept for a minimum of 180 days. Logs are kept in a secure area to prevent tampering. 
  * Statistical data of Customer service usage is kept indefinitely. Logs are kept in a secure area to prevent tampering. 
  * Passwords are not logged.
  * Certain administrative changes to the Services (such as password changes, adding or modifying Customer accounts and settings ) are tracked in an area known as the “Audit” and are available for viewing by a MR administrators only. This information may be provided to Customers on request.
  * MR personnel will not set a defined password for a Customer. Passwords are reset to a random value (which must be changed on first use) and delivered automatically via email to the requesting Customer.

### Intrusion Detection

MR, or an authorized third party, will monitor the Services for unauthorized
intrusions using network-based and/or host-based intrusion detection
mechanisms. MR may analyze data collected by Customers' web browsers (e.g.,
device type, screen resolution, time zone, operating system version, browser
type and version, system fonts, installed browser plug-ins, enabled MIME
types, etc.) for security purposes, including to detect compromised browsers,
to prevent fraudulent authentications, and to ensure that the Services
function properly.

### Security Logs

All systems used in the provision of the Services, including firewalls,
routers, network switches and operating systems, log information to their
respective system log facility or a centralized syslog server (for network
systems) in order to enable security reviews and analysis.

### Incident Management

MR maintains security incident management policies and procedures. MR notifies
impacted customers without undue delay of any unauthorized disclosure of their
respective Customer Data by MR or its agents of which MR becomes aware to the
extent permitted by law. MR publishes system status information on the MR
Support website. MR typically notifies customers of significant system
incidents by email.

### Customer Authentication

Access to Services requires authentication via one of several methods, such as
Customer ID/password, SAML based Federation, or Delegated Authentication as
determined and controlled by the customer. Following successful
authentication, a random session ID is generated and stored in the Customer's
browser to preserve and track session state.

### Physical Security

Production data centers used to provide the Services have access control
systems that permit only authorized personnel to have access to secure areas.
These facilities are designed to withstand adverse weather and other
reasonably predictable natural conditions, utilize redundant electrical and
telecommunications systems, employ environmental systems that monitor
temperature, humidity and other environmental conditions, and contain
strategically placed heat, smoke and fire detection and suppression systems.
Facilities are secured by around-the-clock guards, interior and exterior
surveillance cameras, two-factor access screening and escort-controlled
access. In the event of a power failure, uninterruptible power supply and
continuous power supply solutions are used to provide power while transferring
systems to on-site back-up generators.

### Reliability and Backup

All networking components, network accelerators, load balancers, Web servers
and application servers are configured in a redundant configuration. All
Customer Data submitted to the Services is stored on a primary database server
with multiple active clusters for higher availability. All Customer Data
submitted to the Services is stored on highly redundant carrier-class disk
storage and multiple data paths to ensure reliability and performance. All
Customer Data submitted to the Services, up to the last committed transaction,
is automatically replicated on a near real-time basis to the secondary site
and is backed up on a regular basis. Any backups are verified for integrity
and stored in the same data centers as their instance.

### Disaster Recovery

Production data centers are designed to mitigate the risk of single points of
failure and provide a resilient environment to support service continuity and
performance. The Services utilize secondary facilities that are geographically
diverse from their primary data centers, along with required hardware,
software, and Internet connectivity, in the event MR production facilities at
the primary data centers were to be rendered unavailable. MR has disaster
recovery plans in place and tests them at least once per year. The scope of
the disaster recovery exercise is to validate the ability to failover a
production instance from the primary data center to the secondary data center
utilizing developed operational and disaster recovery procedures and
documentation. The Services’ disaster recovery plans currently have the
following target recovery objectives: (a) restoration of the Covered Service
(recovery time objective) within 12 hours after MR’s declaration of a
disaster; and (b) maximum Customer Data loss (recovery point objective) of 4
hours. However, these targets exclude a disaster or multiple disasters causing
the compromise of both data centers at the same time, and exclude development
and test bed environments, such as the Sandbox service.

### Data Encryption

The Services use industry-accepted encryption products to protect Customer
Data and communications during transmissions between a customer's network and
the Services, including through Transport Layer Encryption (TLS) leveraging
2048-bit RSA server certificates. Additionally, all data, including Customer
Data, is transmitted between data centers for replication purposes across a
dedicated, encrypted link utilizing AES-256 encryption.

### Return of Customer Data

Within 30 days post contract termination, customers may request return of
their respective Customer Data submitted to the Services (to the extent such
data has not been deleted by Customer). MR shall provide such Customer Data
via a downloadable file in comma separated value (.csv) format and attachments
in their native format.

### Deletion of Customer Data

After termination of all subscriptions associated with an environment,
Customer Data submitted to the Services is retained in inactive status within
the Services for 120 days, after which it is securely overwritten or deleted
from production within 90 days, and from backups within 180 days. Physical
media on which Customer Data is stored during the contract term is not removed
from the data centers that MR uses to host Customer Data unless the media is
at the end of its useful life or being deprovisioned, in which case the media
is first sanitized before removal. This process is subject to applicable legal
requirements. Without limiting the ability for customers to request return of
their Customer Data submitted to the Services, MR reserves the right to reduce
the number of days it retains such data after contract termination. MR will
update this MR Security, Privacy and Architecture Documentation in the event
of such a change.

### Analytics

MR may track and analyze the usage of the Services for purposes of security
and helping MR improve both the Services and the Customers experience in using
the Services. For example, we may use this information to understand and
analyze trends or track which of our features are used most often to improve
product functionality. MR may share anonymous usage data with MR’s service
providers for the purpose of helping MR in such tracking, analysis and
improvements. Additionally, MR may share such anonymous usage data on an
aggregate basis in the normal course of operating our business; for example,
we may share information publicly to show trends about the general use of our
services.

### Interoperation with Other Services

The Services may interoperate or integrate with other services provided by MR
or third parties. Security, Privacy and Architecture documentation for
services provided by MR is available in the Trust and Compliance Documentation
section of support.mailroute.net. Additionally, MR may contact Customers to
provide transactional information about the Services. MR offers Customers the
ability to deactivate or opt out of receiving such messages.

