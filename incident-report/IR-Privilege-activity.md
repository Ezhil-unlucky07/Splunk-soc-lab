
## Incident Report — Privilege activity

 Field         Details 

 Incident ID    : IR-2026-001
 Incident Title : Privilege activity
 Date           : 06 Aug 2026 
 Detection Time : 14:32 UTC 
 Severity       : Critical
 Status         : Closed 

## Summary

Splunk triggered an alert detecting account releated activity such as 4720,4732,4672.correlate this event 

## Detection Source

* SIEM Platform: Splunk
* Alert Rule: Privilege activity
## Affected Assets & Identity

* Affected Host Name: PC-01 (PC01.soclab.local)
* Targeted User Account: soc-test-PC-01


## Timeline (07 Aug 2026)

* 14:35:52 UTC:A user account was created.
* 14:37:54 UTC:A member was added to a security-enabled local group.
* 14:39:57 UTC:Special privileges assigned to new logon.

## Investigation Findings

* Source Verification: The analyst reviewed the raw event logs and confirmed that the source IP address was the localhost. No external network connections or remote addresses were involved.
* Failure Count: A total of three failed login attempts occurred within a 7-second window, which automatically triggered the local Windows account lockout policy.
* Activity Context: The localized nature of the failure suggests either a user typo, a misconfigured local service, or an expired cached credential running on the machine.

## Evidence

10/06/2026 10:30:36.590 PM
LogName=Security
EventCode=4720
EventType=0
ComputerName=PC01.soclab.local
SourceName=Microsoft Windows security auditing.
Type=Information
RecordNumber=1831501
Keywords=Audit Success
TaskCategory=File System
OpCode=Info
Message=A user account was created.

10/06/2026 10:30:36.693 PM
LogName=Security
EventCode=4732
EventType=0
ComputerName=PC01.soclab.local
SourceName=Microsoft Windows security auditing.
Type=Information
RecordNumber=1831510
Keywords=Audit Success
TaskCategory=File System
OpCode=Info
Message=A member was added to a security-enabled local group.

10/06/2026 10:36:48.246 PM
LogName=Security
EventCode=4672
EventType=0
ComputerName=PC01.soclab.local
SourceName=Microsoft Windows security auditing.
Type=Information
RecordNumber=1858403
Keywords=Audit Success
TaskCategory=File System
OpCode=Info
Message=Special privileges assigned to new logon.

## Impact

* Normal user were try to gain privilege access in windows which may cause unauthorized changes in windows.


## Response & Mitigation Actions

   1. Alert Triage: The SOC Analyst reviewed and validated the SIEM alert immediately upon receipt.
   2. Origin Analysis: The analyst verified the network logs to ensure no malicious traffic was originating from outside systems.
   3. Identity Verification: The user's account status was monitored until the temporary lockout period expired.
   4. Validation: The analyst verified that the user successfully authenticated with correct credentials after the lockout cooldown ended.

## Recommendations

* Credential Review: Advise the user to audit their active local applications, scripts, or mapped network drives for stored outdated credentials.
* Policy Optimization: Review SIEM correlation rules to adjust alert thresholds if local user typos frequently trigger mid-severity incidents.
* Logon Auditing: Continue monitoring PC-01 to ensure the localized failed logins do not resume systematically.

## Conclusion
The incident is classified as a false positive / benign user error. The failed logon attempts and subsequent lockout resulted entirely from local activity on PC-01, with no indicators of external compromise, brute-force attacks, or malicious lateral movement. The account has been successfully unlocked, normal operations have resumed, and the ticket is now Closed.


