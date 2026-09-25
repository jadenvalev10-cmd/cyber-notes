# Botium Toys: Controls and Compliance Checklist

Internal security audit of Botium Toys, the fictional toy company used as a case study in the Google Cybersecurity Professional Certificate.

## Scope

Using the company's [scope, goals, and risk assessment report](https://docs.google.com/document/d/1s2u_RuhRAI40JSh-eZHvaFsV1ZMxcNSWXifHDTOsgFc/template/preview#heading=h.evidx83t54sc) and the [control categories](https://docs.google.com/document/d/1btezuy_bMKWoK8pd97ZuzdWB9y6au_zfkrpkfVf8ktI/template/preview) reference, I assessed two things:

1. Which security controls Botium Toys currently has in place.
2. Whether it adheres to the best practices of three compliance frameworks: PCI DSS, GDPR, and SOC type 1 and type 2 (see the course reading on [controls, frameworks, and compliance](https://www.coursera.org/learn/foundations-of-cybersecurity/supplement/xu4pr/controls-frameworks-and-compliance)).

## Controls assessment checklist

*Does Botium Toys currently have this control in place?*

| Yes | No | Control |
| :-: | :-: | :-- |
|  | X | Least privilege |
|  | X | Disaster recovery plans |
|  | X | Password policies |
|  | X | Separation of duties |
| X |  | Firewall |
|  | X | Intrusion detection system (IDS) |
|  | X | Backups |
| X |  | Antivirus software |
|  | X | Manual monitoring, maintenance, and intervention for legacy systems |
|  | X | Encryption |
|  | X | Password management system |
| X |  | Locks (offices, storefront, warehouse) |
| X |  | Closed-circuit television (CCTV) surveillance |
| X |  | Fire detection/prevention (fire alarm, sprinkler system, etc.) |

## Compliance checklist

*Does Botium Toys currently adhere to this compliance best practice?*

### Payment Card Industry Data Security Standard (PCI DSS)

| Yes | No | Best practice |
| :-: | :-: | :-- |
|  | X | Only authorized users have access to customers' credit card information. |
|  | X | Credit card information is stored, accepted, processed, and transmitted internally, in a secure environment. |
|  | X | Implement data encryption procedures to better secure credit card transaction touchpoints and data. |
|  | X | Adopt secure password management policies. |

### General Data Protection Regulation (GDPR)

| Yes | No | Best practice |
| :-: | :-: | :-- |
|  | X | E.U. customers' data is kept private/secured. |
| X |  | There is a plan in place to notify E.U. customers within 72 hours if their data is compromised/there is a breach. |
|  | X | Ensure data is properly classified and inventoried. |
|  | X | Enforce privacy policies, procedures, and processes to properly document and maintain data. |

### System and Organization Controls (SOC type 1, SOC type 2)

| Yes | No | Best practice |
| :-: | :-: | :-- |
|  | X | User access policies are established. |
|  | X | Sensitive data (PII/SPII) is confidential/private. |
| X |  | Data integrity ensures the data is consistent, complete, accurate, and has been validated. |
|  | X | Data is available to individuals authorized to access it. |

## Recommendations

**Overall risk score: 8/10 (high)**, driven mainly by gaps in data protection and compliance.

Recommended actions for the IT manager to communicate to stakeholders, in priority order:

1. **Implement least privilege and separation of duties immediately.** Both are quick, low-cost fixes, and they address requirements across PCI DSS, GDPR, and SOC at once.
2. **Encrypt customer credit card data.** Unencrypted cardholder data is a major source of regulatory fine exposure.
3. **Establish backups and a disaster recovery plan.** Without them, a single ransomware attack could halt operations entirely.
4. **Deploy an intrusion detection system and a centralized password management system**, and update the password policy to require stronger passwords.
5. **Classify and inventory assets**, and set a regular maintenance schedule with defined intervention procedures for legacy systems.

**Existing strengths:** the physical controls (locks, CCTV, fire detection), firewall, antivirus software, and the GDPR breach notification plan are in good shape. No action is needed there beyond keeping systems up to date.
