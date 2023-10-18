---
title: Botium Toys Security Audit
---
# Botium Toys Security Audit  
{: .no_toc }

{: .note }
Data Security, Security Policies, Compliance, Risk Analysis, Risk Mitigation, NISF CSF: Identify, Stakeholder Communcation, Documentation
{: .fs-3 }

{::comment}
Data Security
{: .label .label-purple }
Security Policies
{: .label .label-purple }
Compliance
{: .label .label-purple }
Risk Analysis
{: .label .label-purple }
Risk Mitigation
{: .label .label-purple }
NIST CSF: Identify
{: .label .label-purple }
Stakehold Communcation
{: .label .label-purple }
Documentation
{: .label .label-purple }
{:/comment}

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
Botium Toys, a small U.S. toy business with a growing online presence, is facing increasing pressure to support its online market worldwide. To address this, the IT department manager has initiated an internal IT audit to ensure business continuity and compliance as the company expands. Compliance with regulations related to online payments and business operations in the European Union (E.U.) is a priority. The IT manager has started by implementing the NIST CSF, defining audit scope and goals, and conducting a risk assessment. 

Currently, there is inadequate management of assets. Additionally, Botium Toys does not have the proper controls in place and may not be compliant with U.S. and international regulations and standards. 

## Goals & Objectives
Assist the IT manager by:
<ol>
    <li>Suggesting controls based on current company assets</li>
    <li>Review the company's compliance with proper data regulations and standards</li>
    <li>Communicate findings and recommendations clearly to IT manager and stakeholders in a stakeholder memorandum.</li>
</ol>

## Results
### Recommended Controls

<details closed markdown="block">
  <summary>
    Click to view current assets
  </summary>

Assets managed by the IT Department include:
- On-premises equipment for in-office business needs  
- Employee equipment: end-user devices (desktops/laptops, smartphones), remote workstations, headsets, cables, keyboards, mice, docking stations, surveillance cameras, etc.
- Management of systems, software, and services: accounting, telecommunication, database, security, ecommerce, and inventory management
- Internet access
- Internal network
- Vendor access management
- Data center hosting services
- Data retention and storage
- Badge readers
- Legacy system maintenance: end-of-life systems that require human monitoring 
</details>
{: .fs-3 }

| Control name | Type & Description | Category  | Priority  |
|---|---|:---:|:--:|
| Least privilege |Preventative; reduces risk by making sure vendors and non-authorized staff only have access to the assets/data they need to do their jobs | Managerial | High    |
| Disaster recovery plans |Corrective; business continuity to ensure systems are able to run in the event of an incident/there is limited to no loss of productivity downtime/impact to system components | Managerial | High |
| Password policies | Preventative; establish password strength rules to improve security/reduce likelihood of account compromise through brute force or dictionary attack techniques | Managerial | High |
| Access control policies | Preventative; increase confidentiality and integrity of data | Managerial | High |
| Account management policies | Preventative; reduce attack surface and limit overall impact from disgruntled/former employees | Managerial | High |
| Separation of duties | Preventative; ensure no one has so much access that they can abuse the system for personal gain | Managerial | High |
| IDS | Detective; allows IT team to identify possible intrusions quickly | Technical | High
| Encyption | Preventative; makes confidential information/data more secure | Technical | High
| Backups | Corrective; supports ongoing productivity in the case of an event; aligns to the disaster recovery plan | Technical | High
| Lighting | Deterrent; limit “hiding” places to deter threats | Physical | Low
| CCTV surveillance | Preventative/detective; can reduce risk of certain events; can be used after event for investigation | Physical | Medium/Low
| Locking cabinets | Preventative; preventing unauthorized personnel/individuals from physically accessing/modifying network infrastructure gear | Physical | Low

---

### Compliance Review
#### GDPR
{: .no_toc }
{: .fs-5 }
Botium Toys must adhere to GDPR because they operate globally and handle personal data of individuals located within the European Union (EU). GDPR ensures that the company maintains the privacy rights and data protection of EU citizens by establishing strict requirements for the collection, processing, and storage of personal data. 
#### PCI DSS
{: .fs-5 }
{: .no_toc }
Botium Toys must adhere to PCI DSS because they process payment card transactions. Compliance with PCI DSS is necessary to protect the sensitive cardholder data and ensure secure payment processing, reducing the risk of payment card fraud and maintaining customer trust.

---

### Stakeholder Memorandum

TO
: IT Manager, stakeholders

FROM
: Marc De La Cruz

DATE
: October 17, 2023

SUBJECT
: Internal IT audit findings and recommendations

Dear Colleagues,  

Please review the following information regarding the Botium Toys internal audit scope, goals, critical findings, summary and recommendations.

**Audit Scope**

- The following systems will be evaluated: accounting, end point detection, firewalls, intrusion detection system, security information and event management (SIEM) tool. They will be evaluated for current user permissions, implemented controls, and procedures and protocols.
- Ensure current user permissions, controls, procedures, and protocols in place align with GDPR, PCI DSS.
- Ensure current technology is accounted for

**Goals**

- Establish a better process for their systems to ensure they are compliant 
- Fortify system controls
- Implement the concept of least permissions when it comes to user credential management 
- Establish security policies and procedures
- Ensure compliance requirements 

**Critical Findings**

The following system controls must be implemented immediately to strengthen the security posture of the organization:  

- Least privilege controls
- Disaster recovery plans
- Password, access control, and account management policies
- Separation of duties
- Encryption
- Backups
- Password management systems
- Antivirus software
- Manual monitoring, maintenance, and intervention for legacy systems
- Locking cabinets to securely store employee equipment
- Fire detection and prevention to protect physical inventory

Develop and implement polices to ensure compliance with GDPR and PCI DSS in relation to data security of individuals located in the EU and cardholder data and secure payment processing

**Other Findings**

The following should be implemented when possible, but are not critical to the organization’s security posture:
 - Time-controlled safe: reduces impact of physical threats
 - Adequate lighting: limits “hiding” places to deter threats
 - Signage indicating alarm service provider: reduces to likelihood of a successful attack
 - Closed-circuit television (CCTV) surveillance: used to investigative purposes after an incident

**Summary**

 The internal security assessment revealed several critical findings that require immediate attention to strengthen the organization's security posture. It is crucial to implement least privilege controls, disaster recovery plans, and strong password, access control, and account management policies to minimize the risk of data breaches, unauthorized access, and compromised accounts. Separation of duties should be enforced to prevent abuse of system privileges. Intrusion detection systems, encryption, backups, password management systems, and antivirus software are essential for identifying and mitigating threats, ensuring data confidentiality, integrity, and overall system security. Legacy systems require manual monitoring and maintenance to address vulnerabilities.

Additionally, securing employee equipment with locked cabinets and implementing fire detection and prevention measures are necessary to protect physical inventory. To comply with GDPR and PCI DSS, policies must be developed and implemented for data security and secure payment processing. While non-critical findings such as time-controlled safes, adequate lighting, signage indicating alarm service providers, and CCTV surveillance can enhance security, they can be implemented gradually. These findings highlight the importance of implementing robust security controls, policies, and procedures to ensure compliance, protect sensitive data, and safeguard the organization's overall security posture.