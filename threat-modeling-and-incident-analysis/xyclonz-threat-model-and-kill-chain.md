# Xyclonz Threat Modeling & 2025 Incident Reconstruction

## Overview
Synthesizes pre-development threat modeling objectives for the Xyclonz Information System (XIS), a proposed genetic and rare-disease research data platform, with a Diamond Model and Cyber Kill Chain reconstruction of two independent 2025 security incidents affecting Xyclonz.

## Threat Modeling Scope (XIS)
- **System Context:** XIS is scoped around data collection, storage, and processing across clinical, genetic, trial, and registry sources to support rare-disease gene therapy research.
- **Core Modeling Pillars:** Defines security and business objectives, architectural/infrastructure boundaries, asset classification, threat and vulnerability analysis, risk scoring rationale, and defensive controls.

## 2025 Incident Reconstruction (Diamond Model & Cyber Kill Chain)
- **Cryptojacking Campaign (Early 2025 / Jan 31, 2025 Activity):** Targeted legacy IIS infrastructure (`10.0.17763`) and web/file exposure (WebDAV) to deploy mining tooling (`wercplsupporte.dll`, `x.bat`, scheduled persistence) and Monero mining pool communications (`nanopool.org`) on affected hosts (`M5`, `M6`), consuming compute capacity and degrading workloads.
- **Targeted Spear-Phishing & RAT Campaign (March 2025 Activity):** Used public project/personnel reconnaissance on LinkedIn to target researchers on a rare-disease gene therapy initiative via spoofed conference lures, macro/script execution, and remote access activity (`M1`, `M2`, `M3`) aimed at screen capture and research data exfiltration.

## Defensive Takeaways
- Patch legacy web services, disable unnecessary WebDAV/write permissions, and restrict outbound C2/mining pool traffic.
- Harden email authentication and macro/script execution controls, enforce least privilege on researcher workstations, and limit sensitive project exposure on public profiles.
