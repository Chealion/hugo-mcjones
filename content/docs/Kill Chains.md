
---
title: "Kill Chains"
date: 2020-08-25 14:24:43
lastmod: 2022-07-17 11:12:53
categories: ['security']
draft: false
---


# Kill Chains
“a military concept related to the structure of an attack” - Wikipedia


## Lockheed’s Cyber Kill Chain:
The steps a cyberattack always ends up taking

1. Reconnaissance

   Email Addresses, info
2. Weaponization

   Exploit creation
3. Delivery

   Phishing, USB stick, etc.
4. Exploitation

   Exploit vulnerability
5. Installation

   Install malware
6. Command and Control
7. Actions on Objectives


Defensive courses of action can be taken against these phases:[14]

Detect: determine whether an attacker is poking around
Deny: prevent information disclosure and unauthorized access
Disrupt: stop or change outbound traffic (to attacker)
Degrade: counter-attack command and control
Deceive: interfere with command and control
Contain: network segmentation changes

Biggest limitation to this approach is that it does not consider insider threats and lends itself to approaching things as only coming from outside the firewall vs zero trust or other approaches.

——

## MITRE ATT&CK

The ATT&CK framework is more complex than the linear one from Lockheed and has more steps:

1. Initial Access - Used to gain an initial foothold within a network
2. Execution - Technique that results on the execution of code on a local or remote system
3. Persistence - Method used to maintain a presence on the system
4. Privilege Escalation - Result of actions used to gain higher level of permission
5. Defense Evasion - Method used to evade detection or security defenses
6. Credentialed Access - Use of legitimate credential to access system
7. Discovery - Post-compromise technique used to gain internal knowledge of system
8. Lateral Movement - Movement from one system over the network to another
9. Collection - Process of gathering information, such as files, prior to exfiltration
10. Command and Control - Maintaining communication within targeted network
11. Exfiltration - Discovery and removal of sensitive information from a system
12. Impact - Techniques used to disrupt business and operational processes[17]


## Unified Kill Chain
Combines both of the above into 18 steps
https://en.wikipedia.org/wiki/Kill_chain#/media/File:The_Unified_Kill_Chain.png

<!-- #public #security -->

<!-- {BearID:090B5FC9-C301-4D77-81C9-10DEA29794D1-5563-000003A3D605FA71} -->
