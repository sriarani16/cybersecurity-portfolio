# Xyclonz Information System (XIS) — PASTA Threat Model & Risk Assessment

## Overview
Conducted an end-to-end **PASTA (Process for Attack Simulation and Threat Analysis)** threat model for the **Xyclonz Information System (XIS)**, a proposed on-premises private cloud platform for Xyclonz (a New Zealand genetic and rare-disease gene-therapy research organization) supporting ~200 users and batch ingestion of sensitive clinical, genetic, trial, registry, and surveillance datasets[cite: 114, 123, 141, 142].

## Architecture & Critical Assets (PASTA Stages 1–3)
- **Logical Zones & Stack:** On-premises VMware private cloud segmented with a virtual firewall across data collection (External Users, API Gateway, IIS Web Server, Application Server), processing (Apache Spark), and storage (MinIO), with Java/Python/Go components and HTTPS/REST API batch ingestion[cite: 116, 117, 141, 142].
- **Baseline Context:** Modeled as a greenfield system with minimal existing controls (basic virtual firewall segmentation) and prior organizational exposure to a phishing-delivered **Bandook RAT** breach and a **Monero cryptominer** infection on an outdated **IIS 10.0.17763** server (configured in 2018)[cite: 120, 123, 136].
- **Top Critical Assets (out of 14 inventoried assets):**
  - **A6 — IIS Web Server (Impact Score: 25):** Handles internal browser sessions/cookies and authentication; legacy unpatched state and prior Monero compromise create high exposure[cite: 118, 120].
  - **A13 — Sensitive Data (Impact Score: 25):** Includes genetic, clinical/medical, lifestyle, EHR, longitudinal study, surveillance, and rare-disease registry records with only **40% anonymization**, creating high re-identification, regulatory (GDPR-aligned privacy), and reputational risk[cite: 116, 119, 120, 142].

## Threat Library, Simulation & High-Risk Controls (PASTA Stages 4–7)
- **High-Rated Threats (`Intent × Capability` = 25):** Mapped threats across MITRE ATT&CK, OWASP, and CAPEC—including **CAPEC-122** (Privilege Abuse), **T1059** (Command & Scripting Interpreter), **API10:2023** (Unsafe Consumption of APIs), **T1496** (Monero Miner Malware), and **T1005** (Data from Local System)[cite: 124, 125].
- **Attack Simulation & Cyber Kill Chain:** Modeled six attack vectors (`AV1`–`AV6`)—from privilege abuse, weak transport/cookie handling, scripting abuse, and malicious third-party batch API payloads to cryptomining and local file/config harvesting—mapped across Reconnaissance through Actions on Objectives[cite: 132, 133].
- **Risk Scoring & Key Mitigations:** Evaluated 30 vulnerabilities (`V1`–`V30`) against asset impact (`Overall Risk = Probability × Impact`, where High `> 3000` and residual risk equals inherent risk due to no baseline controls)[cite: 135, 136]. Prioritized **RBAC & PAM** for privilege management, **safe serialization & strict input validation** for APIs, **least privilege & sandboxing/bounds checking** for script/memory execution, **strong password hashing & MFA**, **data classification/encryption/logging**, and **outbound filtering & traffic monitoring**[cite: 138, 139].
