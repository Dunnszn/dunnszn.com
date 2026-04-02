---
layout: post
title: "Phishing Incident Response: Containment and Remediation in an Enterprise Environment"
author: "Stephen Dunn"
categories: security
tags: [incident-response, phishing, endpoint-security, active-directory]
image: /assets/images/posts/Phishing-icon.jpg
excerpt: "A real-world phishing incident involving internal account compromise, device isolation, and enterprise-wide remediation."
---

## Overview
In a large enterprise environment, phishing attacks can quickly escalate from a single compromised user to widespread organizational risk. This case study outlines a real-world phishing incident involving internal account misuse, endpoint containment, and coordinated remediation across multiple users.

## Environment
- Hybrid GCC environment  
- Symantec Endpoint Protection  
- Microsoft Outlook  
- Active Directory  

## The Problem
Multiple users reported receiving a suspicious email appearing to come from a legitimate internal employee. The message prompted recipients to sign up for training outside of the official agency learning system.

Several users confirmed they had clicked the link.

This raised immediate concerns:
- potential credential harvesting  
- internal account compromise  
- lateral spread via trusted email identity  

## Investigation
The first priority was identifying the source of the email and containing the threat.

I located the originating user account and worked directly with the user to gather context. The user confirmed:
- they did not intentionally send the email  
- they had previously interacted with a suspicious message  

This strongly indicated account compromise.

At this point, the working assumption shifted from:
> “suspicious email”
to:
> “active internal account misuse”

Immediate actions focused on:
- isolating the user’s endpoint from the network  
- preventing further email propagation  
- preserving the system state for validation  

## Solution
Containment and remediation were executed in parallel.

### Account Containment
- Disabled the user’s ability to send email during investigation  
- Locked down the account in Active Directory  
- Forced credential reset  

### Endpoint Verification
- Performed full antivirus scans using Symantec Endpoint Protection  
- Validated no persistent malware or secondary payloads  
- Confirmed system integrity before returning to service  

### Impact Assessment
- Identified users who interacted with the phishing email  
- Initiated scans on all affected endpoints  
- Verified whether credentials were submitted to the phishing page  

The phishing link redirected users to a Google Form designed to collect usernames and passwords. Fortunately, no confirmed credential submissions were identified.

## Result
The incident was successfully contained without further spread or confirmed credential compromise.

However, the event exposed a critical gap:
> users were still highly susceptible to targeted phishing attempts

As a result:
- collaborated with a vendor to implement simulated phishing campaigns  
- supported development of improved reporting mechanisms for suspicious emails  
- contributed to strengthening user awareness beyond annual compliance training  

## Key Takeaways

- **Assume compromise early**  
  When an internal account sends suspicious emails, treat it as a compromised identity until proven otherwise.

- **Containment speed matters more than certainty**  
  Isolating the device and restricting account activity quickly prevented further spread.

- **User behavior is the primary attack surface**  
  Technical controls alone are not sufficient without continuous user awareness.

- **Phishing attacks often leverage trust, not complexity**  
  The attack succeeded because it appeared to come from a known internal user.

- **Coordination across teams is critical**  
  Effective response required collaboration between endpoint security, identity management, and user support.

- **Incidents should drive improvements, not just resolution**  
  The outcome led to simulated phishing exercises and stronger reporting processes, reducing future risk.