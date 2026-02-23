# NetRCA
AI-assisted network failure timeline reconstruction for TACACS, RADIUS, NTP, and system daemons

## Problem Statement
Network control-plane daemons often fail due to cascading issues across multiple services. 
Manual postmortem analysis of syslog, authentication logs, and daemon crash reports is:

- Time-consuming
- Error-prone
- Hard to scale across multiple subsystems

## Features
- High-performance C-based log parser for TACACS, RADIUS, NTP, and system daemons
- Timeline reconstruction of events leading to failure
- Structured JSON output for AI analysis
- AI-assisted root cause inference
- CLI-based tool for quick analysis

## Architecture Overview


Logs / Syslog
     ↓
+----------------------+
|   NetRCA Engine (C)  |
|  Parser + Timeline   |
+----------+-----------+
           |
    Structured JSON
           v
+----------------------+
|   AI Reasoning Layer  |
|  (Python + LLM API)  |
+----------+-----------+
           |
   Root Cause Report

- C engine: efficient parsing, timeline construction
- Python AI layer: causal reasoning and remediation suggestions
- CLI: one-command analysis and report generation

## Usage

Analyze sample log:

```bash
./netrca analyze samples/sample_syslog.log

===== FAILURE TIMELINE =====
[12:03:21] RADIUS timeout detected
[12:03:22] License expired
[12:03:23] Segmentation fault detected

===== AI ROOT CAUSE =====
Probable Root Cause:
Radius timeout detected and later segfault occured.

Suggested Remediation:
- Verify session ownership before cleanup
- Monitor RADIUS server latency
