RFS Enterprise Cybersecurity Risk Assessment

Windows Server | Active Directory | Cybersecurity GRC | NIST CSF | PowerShell

Project Overview

This project demonstrates the implementation and assessment of cybersecurity controls within a simulated enterprise Windows Server environment.

The fictional organization, RFS, was used to evaluate identity and access management, organizational security policies, account protection, and security auditing.

The project combines hands-on technical configuration with Governance, Risk, and Compliance (GRC) principles to demonstrate how enterprise security controls can be implemented, tested, and evaluated.

Project Type: Cybersecurity GRC Portfolio Lab
Environment: Oracle VirtualBox / Windows Server
Framework: NIST Cybersecurity Framework (CSF)
Status: Core Active Directory configuration and account lockout validation completed.

⸻

1. Project Objectives

The primary objectives of this project were to:

* Establish a simulated enterprise Active Directory environment.
* Implement organizational units (OUs) representing business departments.
* Create and manage domain user accounts and security groups.
* Configure departmental access permissions.
* Implement password and account lockout policies.
* Test account lockout and recovery procedures.
* Enable security auditing and examine Windows security logs.
* Document implemented controls and collect technical evidence.
* Demonstrate the relationship between technical controls and cybersecurity risk management.

⸻

2. Technical Environment

Component	Technology
Virtualization	Oracle VirtualBox
Operating System	Windows Server
Domain Controller	RFS-DC01
Directory Services	Active Directory Domain Services
Administration	Windows PowerShell
Identity Management	Active Directory Users and Computers
Security Policies	Group Policy
Event Monitoring	Windows Event Viewer
Security Auditing	Windows Audit Policy
GRC Framework	NIST CSF 2.0

The environment was created as an isolated virtual laboratory to simulate common enterprise identity management and security administration activities.

⸻

3. Active Directory Organizational Structure

Active Directory was configured to represent an enterprise organizational hierarchy.

Organizational units were created to separate business departments and support centralized user and security administration.

Implementation Activities:

* Created the Active Directory domain controller.
* Established organizational units for business departments.
* Created departmental user accounts.
* Assigned users to appropriate security groups.
* Organized accounts according to departmental responsibilities.

Security Objective: Establish centralized identity management and support role-based access control.

Evidence:

⸻

4. User Account Management

Active Directory user accounts were configured to represent employees within the simulated enterprise.

Administrative activities included:

* Creating domain user accounts.
* Configuring account properties.
* Assigning security group membership.
* Managing account access.
* Verifying account status using PowerShell.

These activities demonstrate fundamental Identity and Access Management (IAM) practices.

Evidence:

⸻

5. Password and Account Lockout Policies

Security policies were configured to reduce risks associated with unauthorized authentication attempts.

Password Policy

Password policy configuration was examined as part of the organization’s authentication security controls.

Security Objectives:

* Enforce organizational password requirements.
* Reduce exposure to weak credentials.
* Support centralized authentication security management.

Evidence:

Account Lockout Policy

An account lockout policy was configured and tested to demonstrate protection against repeated unsuccessful authentication attempts.

Security Configuration

Security Control	Purpose
Account Lockout Threshold	Limits repeated unsuccessful login attempts
Account Lockout Duration	Temporarily restricts access to locked accounts
Reset Lockout Counter	Resets unsuccessful authentication attempts after a configured interval
Account Recovery	Allows authorized administrators to restore account access

Account Lockout Testing

The Active Directory account belonging to Michael Reed (mreed) was used to validate account lockout behavior.

Testing Procedure:

1. Attempted authentication using incorrect credentials.
2. Repeated unsuccessful authentication attempts.
3. Queried the account’s lockout status using PowerShell.
4. Confirmed that Active Directory reported the account as locked.
5. Unlocked the account using administrative PowerShell commands.
6. Verified that the account was no longer locked.

PowerShell Validation

Get-ADUser -Identity mreed -Properties LockedOut |
Select-Object Name,LockedOut

Observed Result Before Recovery:

Name          LockedOut
----          ---------
Michael Reed  True

Administrative Recovery:

Unlock-ADAccount -Identity mreed

Observed Result After Recovery:

Name          LockedOut
----          ---------
Michael Reed  False

Assessment Result: Successful.

The testing demonstrated that Active Directory detected the account lockout condition and that an administrator could restore account access.

Evidence:

⸻

6. Security Auditing and Event Monitoring

Windows security auditing was configured to support the monitoring of account management activities.

Audit Policy Configuration

The Windows Audit Policy utility was used to enable success and failure auditing for the User Account Management subcategory.

Configuration Command:

auditpol /set /subcategory:"User Account Management" /success:enable /failure:enable

Verification Command:

auditpol /get /subcategory:"User Account Management"

Verified Configuration:

Category/Subcategory             Setting
Account Management
  User Account Management        Success and Failure

This configuration enables auditing of supported user account management operations.

Evidence:

Windows Event Viewer

Windows Event Viewer was accessed to examine the Security event log and investigate account-related security events.

Activities Performed:

* Opened Windows Event Viewer.
* Accessed Windows Logs > Security.
* Applied an event filter.
* Attempted to locate Event ID 4740, associated with account lockout events.

Testing Limitation:

Event ID 4740 was not successfully retrieved during the documented investigation.

Therefore, successful generation or collection of this specific event is not claimed.

However, Active Directory account lockout and recovery were independently verified using PowerShell.

Evidence:

⸻

7. Departmental Access Controls

Departmental resources were configured to simulate access restrictions within an enterprise environment.

Activities Performed:

* Created departmental shared folders.
* Configured NTFS permissions.
* Assigned security groups to departmental resources.
* Examined access permissions for organizational users.
* Adjusted permissions during troubleshooting.

Security Objective: Apply least-privilege principles and limit access to resources according to organizational responsibilities.

These configurations illustrate how directory services and file system permissions support enterprise access management.

⸻

8. Cybersecurity Risk Assessment

The implemented security controls address several common enterprise cybersecurity risks.

Identified Risk	Security Control	Risk Management Objective
Unauthorized account access	Account Lockout Policy	Reduce repeated authentication attempts
Weak authentication practices	Password Policy	Strengthen authentication requirements
Excessive user privileges	Security Groups and NTFS Permissions	Enforce least-privilege access
Poor identity administration	Active Directory	Centralize user account management
Limited security visibility	Windows Security Auditing	Improve monitoring capabilities
Unauthorized departmental access	Departmental Resource Permissions	Restrict access to sensitive resources

These controls demonstrate how technical security configurations can support organizational cybersecurity risk treatment.

⸻

9. NIST Cybersecurity Framework Alignment

The project was evaluated using relevant functions from NIST CSF 2.0.

NIST CSF Function	Project Application
Govern (GV)	Security policy and risk management considerations
Identify (ID)	Organizational accounts, resources, and access requirements
Protect (PR)	Active Directory, password policies, account lockout, and access controls
Detect (DE)	Security auditing and Event Viewer investigation
Respond (RS)	Administrative account recovery and troubleshooting

Note: This table describes functional alignment and does not represent a formal NIST CSF compliance certification.

⸻

10. Validation Results

Security Activity	Result
Active Directory domain configuration	Completed
Organizational unit creation	Completed
Domain user account creation	Completed
Security group configuration	Completed
Departmental resource permissions	Configured
Account lockout detection	Verified
Account recovery	Verified
User Account Management auditing	Enabled and verified
Event Viewer access	Completed
Event ID 4740 retrieval	Not verified

The core laboratory objectives were completed, with the documented limitation involving retrieval of the account lockout security event.

⸻

11. Skills Demonstrated

Technical Competencies

* Windows Server administration
* Active Directory Domain Services
* Organizational unit administration
* Identity and Access Management
* Security group administration
* NTFS permissions
* Group Policy configuration
* PowerShell administration
* Windows security auditing
* Security control testing and troubleshooting

Governance, Risk, and Compliance Competencies

* Security control implementation
* Cybersecurity risk identification
* Access control assessment
* Security policy evaluation
* Control validation
* Evidence collection
* Technical documentation
* NIST CSF functional mapping
* Identification of testing limitations

⸻

12. Project Limitations and Future Improvements

The project was conducted in a simulated enterprise environment rather than a production network.

The following improvements could strengthen future assessments:

* Collect and validate additional Windows security event records.
* Introduce dedicated domain-joined client machines.
* Perform additional role-based access testing.
* Develop a formal enterprise risk register.
* Map individual controls to specific NIST CSF 2.0 subcategories.
* Implement centralized log collection.
* Create formal control assessment and risk treatment reports.

⸻

13. Conclusion

The RFS Enterprise Cybersecurity Risk Assessment project demonstrates the implementation and evaluation of foundational enterprise security controls within a Windows Server Active Directory environment.

The project provides hands-on evidence of identity management, security policy configuration, account lockout testing, administrative recovery, and audit policy verification.

By combining technical implementation with cybersecurity risk management principles, the project demonstrates practical competencies relevant to Information Security Analyst, IT Audit, and Governance, Risk, and Compliance roles.

⸻

References

National Institute of Standards and Technology. (2024). The NIST Cybersecurity Framework (CSF) 2.0.

https://doi.org/10.6028/NIST.CSWP.29

Microsoft Learn. Active Directory Domain Services overview.

https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview

Microsoft Learn. Auditpol documentation.

https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/auditpol

⸻

Project Classification: Educational Cybersecurity Laboratory
Organization: RFS (Fictional Enterprise)
Focus: Enterprise Security Controls, Risk Assessment, and GRC
