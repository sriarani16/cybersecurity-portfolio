# Cowrie Honeypot & Network Log Analysis (Splunk SPL)

## Overview
Investigated **1,226,872 JSON log events** in Splunk from a Cowrie/honeypot dataset to profile unique attacker sources, targeted destination ports, successful authentication events, TCP forwarding requests, and timing patterns between failed login attempts[cite: 6, 7, 8, 9].

## Key Findings
- **Unique Source IPs:** Identified **801 unique source IPs** across the full event dataset.
- **Most Targeted Destination Ports:** Across the dataset, the top three destination ports were port **25** (SMTP: **218,755** events, ~38.82%), port **2222** (**146,167** events, ~25.94%), and port **80** (HTTP: **118,283** events, ~20.99%)[cite: 7].
- **Successful Logins & Weak Credentials:** Recorded **5,437** `cowrie.login.success` events, including trivial credentials such as `admin` / `1234` and `mysql` / `mysql`[cite: 7, 8].
- **Direct TCP/IP Forwarding Requests:** Observed **315,375** `cowrie.direct-tcpip.request` events, with top destination IPs including `107.189.171.198` (48,472 events) and `98.138.112.35` (13,586 events).
- **Failed Login Session Cadence:** Aggregated `cowrie.login.failed` events by `session` to calculate session duration and average time per attempt, classifying sessions with an average interval greater than 1 second (`avg_time_per_attempt > 1`) as `"Human"` and `<= 1` second as `"Bot"` (noting that automated tools can also pace requests slower than 1 second).

## Defensive Takeaways
- Enforce strong password policies and disable weak/default credentials rather than relying on obscurity or non-standard ports[cite: 7, 8].
- Restrict outbound/forwarded TCP connections (`direct-tcpip`) and monitor unusual destination IPs and ports (`25`, `2222`, `80`)[cite: 7, 8].
- Combine session-level timing analysis with source IP reputation, failed-attempt volume, and rate limiting to catch both fast automated scanners and slower credential-stuffing sessions[cite: 9].
