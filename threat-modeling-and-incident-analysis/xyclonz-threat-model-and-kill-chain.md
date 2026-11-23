# Xyclonz Threat Modeling & 2025 Incident Reconstruction

## Overview
Synthesizes pre-development threat modeling objectives for the Xyclonz Information System (XIS), a proposed genetic and rare-disease research data platform, with a Diamond Model and Cyber Kill Chain reconstruction of two independent 2025 security incidents affecting Xyclonz.

## Threat Modeling Scope (XIS)
- **System Context:** XIS is scoped around data collection, storage, and processing across clinical, genetic, trial, and registry sources to support rare-disease gene therapy research.
- **Core Modeling Pillars:** Defines security and business objectives, architectural/infrastructure boundaries, asset classification, threat and vulnerability analysis, risk scoring rationale, and defensive controls.

## 2025 Incident Reconstruction (Diamond Model & Cyber Kill Chain)

### 1. Cryptojacking Campaign (Early 2025 / Jan 31, 2025 Activity)
- **Attack Vector & Execution:** Targeted legacy IIS infrastructure (`10.0.17763`) and web/file exposure (WebDAV) to deploy mining tooling (`wercplsupporte.dll`, `x.bat`, scheduled persistence) and Monero mining pool communications (`nanopool.org`) on affected hosts (`M5`, `M6`), consuming compute capacity and degrading workloads.
- **MITRE ATT&CK Alignment:** `T1190` (Exploit Public-Facing Application), `T1505.003` (Web Shell), `T1059.003` (Windows Command Shell), `T1053.005` (Scheduled Task), and `T1496` (Resource Hijacking).

### 2. Targeted Spear-Phishing & Bandook RAT Campaign (March 2025 Activity)
- **Attack Vector & Execution:** Leveraged public project and personnel reconnaissance on LinkedIn to target researchers on a rare-disease gene therapy initiative via spoofed conference lures, macro/script execution, and **Bandook RAT (`S0234`)** remote access activity (`M1`, `M2`, `M3`) aimed at screen capture and research data exfiltration.
- **Bandook (`S0234`) MITRE ATT&CK Mapping:**
  - **Initial Access & Execution:** `T1566.001` (Spearphishing Attachment), `T1204.002` (User Execution: Malicious File), `T1059` (Command and Scripting Interpreter — PowerShell/CMD/VBScript), and `T1106` (Native API).
  - **Defense Evasion:** `T1055.012` (Process Injection: Process Hollowing), `T1140` (Deobfuscate/Decode Files or Information), and `T1027.003` (Steganography).
  - **Discovery & Collection:** `T1083` (File and Directory Discovery), `T1680` (Local Storage Discovery), `T1016` (System Network Configuration Discovery), `T1005` (Data from Local System), `T1113` (Screen Capture), and `T1056.001` (Keylogging).
  - **Command & Control / Exfiltration:** `T1095` (Non-Application Layer Protocol), `T1573.001` (Encrypted Channel: Symmetric Cryptography), `T1105` (Ingress Tool Transfer), and `T1041` (Exfiltration Over C2 Channel).

## Defensive Takeaways
- Patch legacy web services, disable unnecessary WebDAV/write permissions, and restrict outbound C2/mining pool traffic.
- Harden email authentication and macro/script execution controls, enforce least privilege on researcher workstations, and limit sensitive project exposure on public profiles.
