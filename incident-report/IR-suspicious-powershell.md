
## Incident Report — Multiple Failed Authentication Attempts

 Field         Details 

 Incident ID    : IR-2026-001
 Incident Title : Suspicious powershell
 Date           : 04 oct 2026 
 Detection Time : 14:32 UTC 
 Severity       : Low-Medium 
 Status         : Closed 

## Summary
Splunk triggered an alert detecting new process created in windows system.

## Detection Source

* SIEM Platform: Splunk
* Alert Rule: Suspicious powershell

## Affected Assets & Identity

* Affected Host Name: PC-01 (PC01.soclab.local)
* Targeted User Account: soc-test-PC-01

## Timeline (07 Aug 2026)

* 05:41:11 UTC: System created new process


## Investigation Findings

* Source Verification: The analyst reviewed the raw event logs and confirmed that the event done by the localhost user.
* Activity Context: The user check the process that happening in system,its normal behaviour from user.

## Evidence

10/04/2026 05:41:11.247 PM
LogName=Security
EventCode=4688
EventType=0
ComputerName=PC01.soclab.local
SourceName=Microsoft Windows security auditing.
Type=Information
RecordNumber=1752959
Keywords=Audit Success
TaskCategory=File System
OpCode=Info
Message=A new process has been created.

## Impact

* system Impact: No harmful event/process not occured in system
* Confidentiality/Integrity Impact: None. No unauthorized process was execcuted, and no data was exfiltrated.

## Response & Mitigation Actions

   1. Alert Triage: The SOC Analyst reviewed and validated the SIEM alert immediately upon receipt.
   2. Origin Analysis: The analyst verified the network logs to ensure no malicious traffic was originating from outside systems.
   3. Identity Verification: The user's account status was monitored until the temporary lockout period expired.
   4. Validation: The analyst verified that the user successfully authenticated with correct credentials after the lockout cooldown ended.

## Recommendations

* Policy Optimization: Review SIEM correlation rules to adjust alert thresholds if local user typos frequently trigger mid-severity incidents.
* Logon Auditing: Continue monitoring PC-01 to ensure the localized process creation.

## Conclusion
The incident is classified as a false positive. it was normal process created by user.

