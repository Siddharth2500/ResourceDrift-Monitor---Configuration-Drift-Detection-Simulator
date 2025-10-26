# 🚀 ResourceDrift-Monitor — Configuration Drift Detection Between Declared & Actual Infrastructure

![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg?logo=python&logoColor=white)  
![Tool](https://img.shields.io/badge/Drift-Detector-FF5252.svg?logo=alert)  
![Features](https://img.shields.io/badge/Features-Missing%20%7C%20Unexpected%20%7C%20Mismatch-4CAF50.svg?logo=tools)  
![Reports](https://img.shields.io/badge/Reports-JSON-2196F3.svg?logo=json)  
![CI/CD](https://img.shields.io/badge/CI/CD-Ready-2088FF.svg?logo=githubactions)  
![Dependencies](https://img.shields.io/badge/Dependencies-None-green.svg?logo=python)

**ResourceDrift-Monitor** is a **Python 3** tool designed to detect configuration drift between the “declared” infrastructure state (e.g., what’s defined via IaC) and the “actual” deployed state of cloud resources. It’s built for DevOps engineers, SREs, and governance teams, offering clarity on missing resources, unexpected resources, and attribute mismatches.

------

## 🛠 Tech & Languages

| Layer              | Tech / Format                   | Purpose                                      |
|---------------------|---------------------------------|----------------------------------------------|
| Language            | **Python 3.10+**                | Core codebase                                |
| Core Logic          | JSON parsing + comparison logic | Compare declared vs actual states             |
| Reports             | **JSON**                        | Output drift summary and detailed mismatches |
| Execution           | Script / Colab / Notebook       | Flexible usage environment                    |
| Logging             | Console + file write            | Instant summary + persisted audit             |

---

## 🌐 Architecture

Flow:  
1. Step 1 – Load `declared_resources.json`, list of resources that *should* exist.  
2. Step 2 – Load `actual_resources.json`, list of resources that *do* exist in the environment.  
3. Step 3 –  
   - Identify **missing resources** (declared but not actual).  
   - Identify **unexpected resources** (actual but not declared).  
   - For resources present in both: compare attributes (type, region, tags) and record any mismatches.  
4. Step 4 – Build `drift_report.json` summarizing totals and listing all drift findings.  
5. The report can then feed into CI/CD, dashboards, or alerting systems for remediation.

---

## ▶️ Run ResourceDrift-Monitor

```bash
python resource_drift_monitor.py --declared data/declared_resources.json --actual data/actual_resources.json --output data/drift_report.json
