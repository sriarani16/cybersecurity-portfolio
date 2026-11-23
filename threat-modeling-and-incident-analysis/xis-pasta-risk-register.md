# XIS High-Risk Threat & Control Matrix

Summary of high-severity / high-rate risks (`Overall Risk > 3000` in the PASTA assessment) and mapped controls for **A13 (Sensitive Data)** and **A6 (IIS Web Server)**.
| Target Asset | Threat | Key Vulnerability / Weakness | Core Mitigations |
| :--- | :--- | :--- | :--- |
| **A13: Sensitive Data** | Privilege Abuse (`CAPEC-122`) | Improper Privilege Management (`CWE-269`) | Enforce RBAC, deploy PAM tools, and run periodic access/privilege reviews. |
| **A13: Sensitive Data** | Unsafe Consumption of APIs (`API10:2023`) | Deserialization of Untrusted Data (`CWE-502`), Code Injection (`CWE-94`), Prototype Pollution (`CWE-1321`)| Use safe serialization, validate/sanitize inputs, freeze/clone objects or avoid `eval()`, and conduct code reviews/security testing. |
| **A13: Sensitive Data** | Data from Local System (`T1005`) | Exposure of Sensitive Information (`CWE-200`), Insufficiently Protected Credentials (`CWE-522`)| Enforce data classification, access policies, encryption at rest/in transit, access logging, strong hashing, MFA, and no hardcoded secrets. |
| **A6: IIS Web Server** | Command & Scripting Interpreter (`T1059`) | Improper Privilege Management (`CWE-269`), Memory Buffer Bounds (`CWE-119`) | Run scripts under least privilege, isolate/sandbox execution, monitor admin scripts, and use memory-safe code/bounds checks/stack canaries. |
| **A6: IIS Web Server** | Monero Miner Malware (`T1496`) | Use of Unmaintained Third-Party Components (`CWE-1104`) | Patch/update components, filter outbound requests, restrict lateral/internal paths from the web server, and monitor traffic anomalies. |
