#Detecting Lateral Movement in Windows Event Logs

**Purpose**

To detect authentication-based lateral movement in Windows envrionments

**Data Required**

Windows Security logs, specifically:

* Successful Logon (ID 4624)
* Failed Logon (ID 4625)
* Kerberos Authentication (ID 4768)
* Kerberos Service Ticket (ID 4776)
* Assignment of Administrator Rights (ID 4672)
* Unknown username or password (ID 529)
* Account logon time restriction violation (ID 530)
* Account currently disabled (ID 531)
* User account has expired (ID 532)
* User not allowed to logon to the computer (ID 533)
* User has not been granted the requested logon type (ID 534)
* The account's password has expired (ID 535)
* The NetLogon component is not active (ID 536)
* The logon attempt failed for other reasons (ID 537)
* Account lockout (ID 539)
* User initiated logon (ID 4647)
* Workstation locked (ID 4800)
* Workstation unlocked (ID 4801)

Logon Failure Events:

* User name does not exist (ID 0xC0000064)
* User name is correct but the password is wrong (ID 0xC000006A)
* User is currently locked out (ID 0xC0000234)
* Account is currently disabled (ID 0xC0000072)
* User tried to logon outside his day of week or time of day restrictions (ID 0xC000006F)
* Workstation restriction (ID 0xC0000070)
* Account expiration (ID 0xC00000193)
* Expired password (ID 0xC0000071)
* Clocks between DC and other computer too far out of sync (ID 0xC0000133)
* User is required to change password at next logon (ID 0xC0000224)
* Evidently a bug in Windows and not a risk (ID 0xC0000225)
* "The user has not been granted the requested logon" (ID 0xC000015b)

User Account changes

* Created (ID 4720)
* Enabled (ID 4722)
* User changed own password (ID 4723)
* Privileged User changed this user’s password (ID 4724)
* Disabled (ID 4725)
* Deleted (ID 4726)
* Changed (ID 4738)
* Locked out (ID 4740)
* Unlocked (ID 4767)
* Name change (ID 4781)

**Collection Considerations**

Not all of these events are enabled by default, so you may need to
change your audit policy

**Analysis Techniques**

Stack counting, outlier detection, visualization

**Description**

Make note of administrative attempts, visualize this activity and look for deviations from baseline in the number of attempts, the accounts involved in the attempts or the computers on which the attempts occur.

**Other Notes**

"Administrative" accounts includes any user with special rights, not necessarily only the Local or Domain "Administrator" accounts.

**More Info**

- [Detecting Lateral Movement in APTs: Analysis Approach on Windows Event Logs](https://www.first.org/resources/papers/conf2016/FIRST-2016-105.pdf), Shingo ABE, JPCERT/CC
- [Seek Evil, and Ye Shall Find: A Guide to Cyber Threat Hunting Operations](https://digitalguardian.com/blog/seek-evil-and-ye-shall-find-guide-cyber-threat-hunting-operations), Tim Bandos, Digital Guardian

