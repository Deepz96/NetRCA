NetRCA is composed of two main components:

1. **C Engine**
   - Parses multiple network logs (TACACS, RADIUS, CRASH)
   - Normalizes log lines into structured events
   - Builds a chronological timeline
   - Detects failures and cascading anomalies
   - Exports events as JSON for AI analysis

2. **AI Reasoning Layer (Python)**
   - Consumes JSON timeline
   - Infers probable root causes
   - Suggests remediation steps
