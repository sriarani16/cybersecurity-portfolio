# XIS High-Risk Threat & Control Matrix

Summary of high-severity / high-rate risks (`Overall Risk > 3000` in the PASTA assessment) and mapped controls for **A13 (Sensitive Data)** and **A6 (IIS Web Server)**[cite: 119, 120, 135, 138, 139].

| Target Asset | Threat | Key Vulnerability / Weakness | Core Mitigations |
| :--- | :--- | :--- | :--- |
| **A13: Sensitive Data**[cite: 119, 120] | Privilege Abuse (`CAPEC-122`)[cite: 124, 138] | Improper Privilege Management (`CWE-269`)[cite: 126, 130, 138] | Enforce RBAC, deploy PAM tools, and run periodic access/privilege reviews[cite: 138]. |
| **A13: Sensitive Data**[cite: 119, 120] | Unsafe Consumption of APIs (`API10:2023`)[cite: 124, 138] | Deserialization of Untrusted Data (`CWE-502`), Code Injection (`CWE-94`), Prototype Pollution (`CWE-1321`)[cite: 127, 130, 138] | Use safe serialization, validate/sanitize inputs, freeze/clone objects or avoid `eval()`, and conduct code reviews/security testing[cite: 138]. |
| **A13: Sensitive Data**[cite: 119, 120] | Data from Local System (`T1005`)[cite: 124, 138] | Exposure of Sensitive Information (`CWE-200`), Insufficiently Protected Credentials (`CWE-522`)[cite: 128, 130, 138] | Enforce data classification, access policies, encryption at rest/in transit, access logging, strong hashing, MFA, and no hardcoded secrets[cite: 138]. |
| **A6: IIS Web Server**[cite: 118, 120] | Command & Scripting Interpreter (`T1059`)[cite: 124, 139] | Improper Privilege Management (`CWE-269`), Memory Buffer Bounds (`CWE-119`)[cite: 127, 130, 139] | Run scripts under least privilege, isolate/sandbox execution, monitor admin scripts, and use memory-safe code/bounds checks/stack canaries[cite: 139]. |
| **A6: IIS Web Server**[cite: 118, 120] | Monero Miner Malware (`T1496`)[cite: 124, 139] | Use of Unmaintained Third-Party Components (`CWE-1104`)[cite: 128, 130, 139] | Patch/update components, filter outbound requests, restrict lateral/internal paths from the web server, and monitor traffic anomalies[cite: 128, 139]. |
