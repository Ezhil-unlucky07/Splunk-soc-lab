
## Incident Report — Multiple Failed Authentication Attempts

 Field         Details 

 Incident ID    : IR-2026-001
 Incident Title : Multiple Failed Authentication Attempts 
 Date           : 07 Aug 2026 
 Detection Time : 14:32 UTC 
 Severity       : Low-Medium 
 Status         : Closed 

## Summary
Splunk triggered an alert detecting repeated failed authentication attempts against a local Windows account. Investigation confirmed the activity originated entirely from the local host.
## Detection Source

* SIEM Platform: Splunk
* Alert Rule: Multiple Failed Authentication Attempts

## Affected Assets & Identity

* Affected Host Name: PC-01 (PC01.soclab.local)
* Targeted User Account: soc-test-PC-01
* Source IP Address: 127.0.0.1 (Localhost)

## Timeline (07 Aug 2026)

* 14:35:52 UTC: First failed authentication attempt detected.
* 14:35:54 UTC: Second failed authentication attempt detected.
* 14:35:57 UTC: Third failed authentication attempt detected.

## Investigation Findings

* Source Verification: The analyst reviewed the raw event logs and confirmed that the source IP address was the localhost. No external network connections or remote addresses were involved.
* Failure Count: A total of three failed login attempts occurred within a 7-second window, which automatically triggered the local Windows account lockout policy.
* Activity Context: The localized nature of the failure suggests either a user typo, a misconfigured local service, or an expired cached credential running on the machine.

## Evidence

Date/Time: 07 Aug 2026 14:35:59 UTC
LogName=Security
EventCode=4625
EventType=0
ComputerName=PC01.soclab.local
SourceName=Microsoft Windows security auditing.
Type=Information
RecordNumber=1694297
Keywords=Audit Failure
TaskCategory=Logon
OpCode=Info
Message=An account failed to log on.

## Impact

* Availability Impact: The soc-test-PC-01 account was temporarily locked out. The authorized user was briefly unable to authenticate or access local resources despite having the correct credentials.
* Confidentiality/Integrity Impact: None. No unauthorized access was gained, and no data was exfiltrated.

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


