                 ┌──────────────┐
                 │    Kali      │
                 │ Lab Activity │
                 └──────┬───────┘
                        │
                        ▼
┌─────────────────────────────────────┐
│          Windows 11 Endpoint        │
│                                     │
│ Windows Security Logs               │
│ PowerShell Logs                     │
│ Sysmon Logs                         │
└──────────────────┬──────────────────┘
                   │
                   │ Log Collection
                   ▼
          ┌─────────────────┐
          │     Splunk      │
          │      SIEM       │
          ├─────────────────┤
          │ SPL Searches    │
          │ Detections      │
          │ Dashboards      │
          │ Alerts          │
          └────────┬────────┘
                   │
                   ▼
          Investigation
                   │
                   ▼
            Incident Report

