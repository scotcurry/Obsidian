Try to get the deck
Security Labs - Check it out

Good fit for low cloud security maturity.  Maturity levels: 1) No security team (CTO is the security person), 2) Small security team (<5 security IC, CTO is still the security person jack of all trades, champion is full stack engineer), 3) Siloed security (CISO, champion is based on the product), 4) Enterprise engineering team (champion is Engineering lead).

Other tools in the space - Splunk, IBM QRadar, and Sumo Logic.  Very hard to learn tools, so this is a greenfield type customer.

Small Security Teams - use Cloud native security tools, and they CNAPP (Cloud Native), Orca Security, Wiz, and Lacework.  Get through compliance audits,

Siloed Enterprise Security - Specialized solutions integrated in a central SIEM / SOAR.  This is the part of the market that we don't really want to deal with.  Crowdstrike does this, can you?

1-No security (commercial, mid-market) - Before scenario the customer cannot detect when it is targeted.  Value question - Walk me through the last time they were attacked and how did they detect it?  Let's say tomorrow one of your engineers makes an S3 bucket available.  What do you do?  After scenario - Customer can respond to the attack.

2-Small security team - Before scenario team struggles to get their engineering team to respond.  How many different cloud accounts / regions do you operate?  How hard has it been to act of cloud native security solution findings?  Walk me through the last attack you had to investigate.  How did you figure out if the attack was successful.  After scenario - teams are empowered to fix misconfigurations and stack on their own

3-Siloed Enterprise Security Team (proceed with care) - replacing everything is just not feasible.  How would you detect if an attacker spins up a shell on one of your containers? trigger a SSRF vulnerabilty on your APIs, enumerate S3 buckets.  A tool for every use case.  Datadog can correlate your data.  After scenario customer gets real time security.

Make sure we already getting their data into Datadog, set expectations with high urgency customers.