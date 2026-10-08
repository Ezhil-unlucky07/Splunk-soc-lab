# Splunk SOC Lab

## Objective

Simulate a attacks to windows system.
collect windows security logs from endpoint using splunk universal forwarder and forward those to splunk server/indexer.
detect the alert using SPL(Search processing language).

## Architecture

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

## Technologies

- Windows 11
- Ubuntu Server
- Splunk
- Sysmon
- Windows Event Logs

## Detection Scenarios

  Failed authentication
  Suspicious PowerShell
  Privileged group modification

## SOC Workflow

Generate Event
      ↓
Collect Logs
      ↓
forward splunk server/indexer
      ↓
SPL(Search processing language)
      ↓
Investigation
      ↓
Incident Report
      
