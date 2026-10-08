# Investigation - Privilege activity

## Alert

Suspicious powershell in windows system.

## Detection Time

   Date : 9/10/2026/
   Time : 13:39

## Affected Host

  Host: PC01

## Account

account name : soc-lab

## Source

[IP : localhost ]

## Timeline

  14:35:52 UTC:A user account was created.
  14:35:54 UTC:A member was added to a security-enabled local group.
  14:35:57 UTC:Special privileges assigned to new logon.

## Evidence

- Event ID 4720,4728,4672

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

