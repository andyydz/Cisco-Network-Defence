Access Control

Cisco Network Defense — Module 3

Overview

Access control is the process of controlling who or what can access systems, networks, applications, files, and other organizational resources.

Effective access control combines authentication, authorization, and accounting (AAA) with appropriate policies, technologies, and security models.

This module covers physical, logical, and administrative access control, authentication technologies, authorization models, Network Access Control (NAC), account management, AAA, and modern approaches such as Zero Trust and Federated Identity Management.

1. Why Access Control Matters

Organizations need to ensure that users and systems can access only the resources required for their legitimate activities.

Effective access control helps organizations:

Prevent unauthorized access
Protect sensitive information
Enforce least privilege
Separate administrative responsibilities
Track user activity
Support compliance
Reduce the impact of compromised accounts

A simplified access-control process is:

Identity
   ↓
Authentication
   ↓
Authorization
   ↓
Access
   ↓
Accounting / Auditing
2. Types of Access Control

Access control can be divided into several categories.

2.1 Physical Access Control

Physical access control protects physical locations and infrastructure.

Examples include:

Locks
Access cards
Badges
Biometric systems
Security guards
Surveillance
Restricted areas

The objective is to prevent unauthorized individuals from physically accessing systems or facilities.

2.2 Logical Access Control

Logical access control protects digital resources.

Examples include:

Usernames and passwords
Multi-factor authentication
Access-control lists
File permissions
Network authentication
Application permissions
Account restrictions

Logical access control determines whether a user or system can access a digital resource.

2.3 Administrative Access Control

Administrative access control consists of organizational policies, procedures, and processes used to manage access.

Examples include:

Security policies
Procedures
Hiring practices
Background checks
Data classification
Security training
Security reviews

Administrative controls establish the organizational rules that support technical and physical access controls.

3. Administrative Access Control

Administrative controls are particularly important because access should be managed throughout the employee lifecycle.

A simplified process is:

Hiring
  ↓
Background Verification
  ↓
Access Assignment
  ↓
Security Training
  ↓
Periodic Review
  ↓
Role Change / Access Modification
  ↓
Termination / Access Removal

This helps ensure that users receive appropriate access and that unnecessary permissions are removed when they are no longer required.

3.1 Hiring Practices

Organizations can incorporate security considerations into hiring processes.

Examples include:

Verifying candidate information
Defining security responsibilities
Determining required access
Establishing acceptable-use expectations
3.2 Background Checks

Background checks can help organizations assess candidates for roles involving sensitive information or privileged access.

The specific requirements depend on organizational policies and applicable laws.

3.3 Data Classification

Data classification identifies the sensitivity and importance of information.

Classification can help determine:

Who can access information
How information should be stored
How information should be transmitted
How information should be protected
How long information should be retained
3.4 Security Training

Users should understand their responsibilities when accessing organizational systems.

Security awareness can address:

Password security
Phishing
Acceptable use
Data handling
Authentication
Incident reporting
Device security
3.5 Security Reviews

Access should be periodically reviewed to identify:

Unnecessary permissions
Excessive privileges
Inactive accounts
Role changes
Policy violations

Regular access reviews support the principle of least privilege.

4. Authentication, Authorization, and Accounting

AAA is one of the central concepts in access control.

Authentication → Who are you?
Authorization  → What are you allowed to do?
Accounting     → What did you do?
4.1 Authentication

Authentication verifies the identity of a user, device, or system.

Common authentication factors include:

Something You Know

Examples:

Password
PIN
Passphrase
Something You Have

Examples:

Smart card
Security token
Mobile authentication device
Something You Are

Examples:

Fingerprint
Iris
Facial characteristics
4.2 Authorization

Authorization determines which resources an authenticated identity is permitted to access.

For example:

User
  ↓
Authenticated
  ↓
Authorization Check
  ↓
Allowed Resource

Authentication does not automatically provide unrestricted access.

4.3 Accounting

Accounting records activity performed by users or systems.

Accounting can record:

Login activity
Commands
Network connections
Resource usage
Administrative actions
Session duration

Accounting provides visibility that can support security monitoring and investigations.

5. Federated Identity Management

Federated Identity Management allows identities to be recognized across multiple trusted systems or organizations.

Instead of maintaining completely separate identities for every service, federated systems can allow an identity provider to authenticate a user and provide trusted identity information to other services.

Conceptually:

User
  ↓
Identity Provider
  ↓
Authentication
  ↓
Trusted Service
  ↓
Authorized Access

Federated identity can simplify identity management while reducing the need for users to maintain separate credentials across every service.

6. Multi-Factor Authentication

Multi-Factor Authentication (MFA) requires multiple authentication factors.

For example:

Password
   +
Authentication Code

or:

Password
   +
Biometric

MFA improves security because compromise of a single authentication factor does not necessarily provide complete access.

7. Zero Trust Security

Zero Trust is based on the principle that access should not automatically be trusted based solely on network location.

A simplified principle is:

Never automatically trust; continuously verify.

Access decisions can consider:

Identity
Device
Resource
Context
Risk
Security policy
7.1 Zero Trust Workforce

Zero Trust can be applied to users regardless of where they work.

Users should be authenticated and authorized based on their identity, device, access requirements, and security context.

7.2 Zero Trust Workload

Workloads such as applications, services, containers, and APIs can also require identity-based access controls.

Communication between workloads should not automatically be trusted simply because they operate within the same environment.

7.3 Zero Trust Workplace

The workplace can include traditional offices, remote environments, cloud services, and other locations.

Access should be based on verified identity and appropriate authorization rather than assuming that a particular network location is inherently trusted.

8. Access Control Models

Access control models define how permissions are assigned and enforced.

8.1 Discretionary Access Control (DAC)

In DAC, resource owners can control access to their resources.

Advantages can include flexibility.

However, decentralized permission management can create challenges when permissions become difficult to control consistently.

8.2 Mandatory Access Control (MAC)

MAC uses centrally defined security policies and classifications to control access.

Users generally cannot freely change permissions.

MAC is commonly associated with environments requiring strict security policies.

8.3 Role-Based Access Control (RBAC)

RBAC assigns permissions based on roles.

User
  ↓
Role
  ↓
Permissions

For example:

Administrator → Administrative Permissions
Analyst       → Analysis Permissions
Employee      → Standard User Permissions

RBAC can simplify access management in organizations with clearly defined job roles.

8.4 Attribute-Based Access Control (ABAC)

ABAC makes authorization decisions based on attributes.

Attributes can include:

User identity
Role
Device
Location
Resource
Time
Security context

This can provide more granular access decisions than role-based permissions alone.

8.5 Rule-Based Access Control

Rule-based access control uses predefined rules to determine whether access should be allowed.

Example:

IF condition is satisfied
        ↓
Allow access

ELSE
        ↓
Deny access

Rules can be based on factors such as:

Network location
Time
Protocol
Security requirements
Resource type
9. Network Access Control (NAC)

Network Access Control systems control whether devices are permitted to connect to a network.

A NAC system can evaluate factors such as:

User identity
Device identity
Device security posture
Authentication status
Security policy compliance

A simplified process is:

Device Attempts Connection
          ↓
      NAC Check
          ↓
 Authentication
          ↓
 Security Assessment
          ↓
   Policy Evaluation
       ↙       ↘
    Allow      Deny

NAC can help organizations prevent unauthorized or non-compliant devices from gaining unrestricted network access.

10. Account Management

Account management ensures that user and system accounts are created, maintained, monitored, and removed appropriately.

10.1 Account Types

Organizations may maintain different account types based on purpose and privilege.

Examples include:

Standard user accounts
Administrative accounts
Service accounts
Guest accounts
System accounts

Each account should have only the permissions required for its intended purpose.

10.2 Privileged Accounts

Privileged accounts have elevated permissions.

Examples include:

System administrators
Network administrators
Database administrators
Security administrators

Because privileged accounts can make significant changes, they require stronger controls and monitoring.

Security practices can include:

MFA
Least privilege
Separate administrative accounts
Logging
Regular review
Restricted access
11. File Access Control

File access control determines who can access, modify, execute, or delete files.

Permissions can commonly include:

Read
Write
Execute
Modify
Delete

Effective file permissions should follow the principle of least privilege.

12. Windows Account Policies

Operating systems can enforce policies that control account behavior.

12.1 Password Policy

Password policies can define requirements such as:

Password length
Password complexity
Password history
Password expiration
Account security requirements
12.2 Account Lockout Policy

Account lockout policies can restrict access after repeated unsuccessful authentication attempts.

This can help reduce certain brute-force attack attempts.

12.3 Audit Policy

Audit policies determine which security-related activities should be recorded.

Examples include:

Login events
Account changes
Privilege use
Policy changes
System events

Audit data can support monitoring and investigation.

13. Authentication Technologies

The module covered several authentication protocols and technologies.

13.1 EAP

The Extensible Authentication Protocol (EAP) provides a framework for supporting different authentication mechanisms.

Examples include:

EAP-TLS
PEAP
EAP-TTLS
EAP-FAST
13.2 PAP

Password Authentication Protocol (PAP) is a simple authentication protocol.

Because credentials can be transmitted without strong protection in its basic implementation, PAP should not be considered appropriate for environments requiring strong credential confidentiality unless protected by an appropriate secure channel.

13.3 CHAP

Challenge Handshake Authentication Protocol (CHAP) uses a challenge-response mechanism rather than directly transmitting the password in plaintext.

It provides stronger protection than basic plaintext password transmission, although modern authentication requirements may call for more advanced mechanisms.

14. Authentication Servers
14.1 RADIUS

Remote Authentication Dial-In User Service (RADIUS) provides centralized authentication, authorization, and accounting services.

It is commonly used in network-access environments.

14.2 TACACS+

Terminal Access Controller Access-Control System Plus (TACACS+) is an AAA protocol commonly associated with centralized authentication and authorization for network device administration.

It separates authentication and authorization functions and provides detailed control over administrative access.

14.3 Kerberos

Kerberos is a network authentication protocol that uses tickets to authenticate users and services.

It is designed to provide secure authentication within trusted environments.

15. Cryptographic Hash Functions

Cryptographic hash functions are mathematical functions that produce a fixed-length output from input data.

They are used in security applications such as:

Integrity verification
Password protection mechanisms
Digital signatures
Authentication systems
HMAC

A simplified model is:

Data
 ↓
Hash Function
 ↓
Fixed-Length Hash

A secure cryptographic hash function should make it computationally difficult to derive the original input or find another input producing the same relevant hash output.

16. Hash-Based Message Authentication Code

HMAC combines a cryptographic hash function with a secret key.

Conceptually:

Message + Secret Key
        ↓
     HMAC Function
        ↓
Authentication / Integrity Value

HMAC can provide assurance that:

The message was not modified
The message was generated by a party possessing the shared secret

HMAC is therefore useful for authentication and integrity protection.

17. Access Control Strategies

Different access-control strategies provide different levels of flexibility and centralization.

Mandatory Access Control

Permissions are centrally controlled according to security policies.

Discretionary Access Control

Resource owners have greater control over permissions.

Role-Based Access Control

Permissions are associated with organizational roles.

Attribute-Based Access Control

Access decisions are based on multiple attributes.

Rule-Based Access Control

Access decisions are determined by predefined rules.

The appropriate model depends on the organization's requirements, security policies, and operational environment.

18. AAA Usage and Operation

AAA provides a structured approach to managing access.

Authentication
     ↓
"Who are you?"
     ↓
Authorization
     ↓
"What are you allowed to do?"
     ↓
Accounting
     ↓
"What did you do?"

This model provides both access control and visibility into user activity.

19. AAA Authentication

AAA authentication can be implemented using different approaches.

19.1 Local Authentication

Authentication information is stored locally on the device or system.

Advantages can include:

Simple deployment
No external authentication server required

However, managing credentials across many devices can become difficult.

19.2 Server-Based Authentication

Authentication is handled by a centralized authentication server.

Examples include:

RADIUS
TACACS+

Centralized authentication can simplify:

Account management
Policy enforcement
Credential management
Auditing
20. AAA Accounting

AAA accounting records information about user and system activity.

Accounting can provide visibility into:

Network connections
Commands
Sessions
Resource usage
System activity
20.1 Network Connection Accounting

Records information about network sessions and connections.

Possible information includes:

User
Session start
Session end
Connection type
Resource accessed
20.2 System Accounting

Tracks system-level activity and events.

20.3 Command Accounting

Records commands executed by users, particularly privileged users.

This can help security teams determine what administrative actions were performed.

20.4 Resource Accounting

Tracks the use of organizational resources.

Examples can include:

Network bandwidth
Storage
Processing resources
Services

Accounting provides an audit trail that can support security investigations and operational monitoring.

21. Access Control Architecture

The concepts covered in this module can be combined into a layered access-control architecture:

                    ACCESS CONTROL
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
        ▼                 ▼                 ▼
    Physical           Logical        Administrative
     Access             Access            Controls
        │                 │                 │
        └─────────────────┼─────────────────┘
                          ▼
                   Authentication
                          │
                          ▼
                    Authorization
                          │
                          ▼
                     Resource
                      Access
                          │
                          ▼
                     Accounting
                          │
                          ▼
                   Audit / Review

This demonstrates that access control is not simply a username-and-password mechanism.

It is a combination of identity management, policy, authorization, monitoring, and accountability.

22. Security Principle: Least Privilege

A fundamental access-control principle is least privilege.

Users, applications, and systems should receive only the permissions necessary to perform their legitimate functions.

For example:

Required Permission
        ↓
      Granted

Unnecessary Permission
        ↓
       Denied

Least privilege can reduce the potential impact of:

Compromised accounts
Insider threats
Malware
Privilege abuse
Configuration errors
23. Security Principle: Separation of Duties

Separation of duties divides sensitive responsibilities between different individuals or roles.

For example:

User A → Requests Change
User B → Approves Change
User C → Implements Change

This reduces the risk of a single individual having complete control over a sensitive process.

24. Cybersecurity and SOC Relevance

Access control is highly relevant to Security Operations Center activities.

SOC analysts may investigate:

Failed login attempts
Suspicious authentication
Privilege escalation
Unauthorized access
Account compromise
Unusual administrative activity
Network authentication events
Access-control violations

AAA accounting and audit logs can provide important evidence during investigations.

A simplified SOC workflow is:

Authentication Event
        ↓
Log Generation
        ↓
Centralized Monitoring
        ↓
Detection
        ↓
Investigation
        ↓
Incident Response

Understanding access control therefore helps connect identity management with security monitoring and incident response.

25. Key Takeaways

After completing this module, I developed an understanding of:

Physical, logical, and administrative access control
Administrative security practices
Hiring and background verification
Data classification
Security training and access reviews
Authentication
Authorization
Accounting
Federated Identity Management
Multi-Factor Authentication
Zero Trust security
Zero Trust for workforce, workloads, and workplace environments
DAC
MAC
RBAC
ABAC
Rule-Based Access Control
Network Access Control systems
Account management
Privileged accounts
File access control
Windows password policies
Account lockout policies
Audit policies
EAP
PAP
CHAP
RADIUS
TACACS+
Kerberos
Cryptographic hash functions
HMAC
AAA architecture
Local authentication
Server-based authentication
AAA accounting
Network connection accounting
System accounting
Command accounting
Resource accounting
Least privilege
Separation of duties
26. Conclusion

Access control is a fundamental component of cybersecurity because protecting systems requires more than simply knowing who a user is.

A complete access-control architecture must answer three questions:

Who are you?
     ↓
What are you allowed to access?
     ↓
What did you do?

Authentication establishes identity, authorization determines permitted actions, and accounting provides visibility into activity.

Modern access-control architectures increasingly combine these principles with:

Multi-Factor Authentication
Zero Trust
Federated Identity
Network Access Control
Role and attribute-based authorization
Centralized authentication
Continuous monitoring
Least privilege

Together, these controls help organizations reduce unauthorized access, limit the impact of compromised identities, and maintain visibility into security-relevant activity.

Course Information

Course: Cisco Network Defense
Module: 3 — Access Control
Primary Focus: Authentication, Authorization, Accounting, Identity Management, Access-Control Models, Network Access Control, and Security Monitoring
