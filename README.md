# 🛡️ Insider Threat Matrix

> A custom MITRE ATT&CK®-style framework for computer-enabled insider threat detection and investigation.

![Tactics](https://img.shields.io/badge/Tactics-8-4f8ef7?style=flat-square)
![Techniques](https://img.shields.io/badge/Techniques-50-7c6cf5?style=flat-square)
![Detections](https://img.shields.io/badge/Detection%20Mappings-130%2B-34c759?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-orange?style=flat-square)

---

## 📖 Overview

This framework structures insider threat detection using the same taxonomy approach as [MITRE ATT&CK®](https://attack.mitre.org) — tactics as columns, techniques as cells, detections mapped beneath each technique — but built specifically for the insider threat problem space.

Where ATT&CK focuses on external adversary actions, this matrix is **behavior-first**: it captures how insiders collect, stage, and exfiltrate data, how they cover their tracks, and how defenders should correlate signals, validate context, and escalate through a governance layer.

The interactive HTML file can be opened locally or hosted via GitHub Pages with no dependencies or server required.

---

## 🗂️ Repository Structure

```
insider-threat-matrix/
├── insider-threat-matrix.html   # Full interactive matrix (self-contained)
└── README.md                    # This file
```

---

## ⚡ Quick Start

**Option 1 — Open locally:**
```bash
git clone https://github.com/YOUR_USERNAME/insider-threat-matrix.git
cd insider-threat-matrix
open insider-threat-matrix.html   # macOS
# or just double-click the file in Windows/Linux
```

**Option 2 — Host on GitHub Pages:**
1. Go to your repo → **Settings → Pages**
2. Set source to **Deploy from branch → main → / (root)**
3. Your matrix will be live at `https://YOUR_USERNAME.github.io/insider-threat-matrix/`

---

## 🧱 Framework Structure

The matrix is organized into **8 tactics** representing the full insider threat lifecycle:

| # | Tactic | Description |
|---|--------|-------------|
| T0 | **Initial Risk Conditions** | Precursor state amplifiers — not standalone triggers, used as risk context |
| T1 | **Collection** | Data access and staging behaviors indicating unauthorized collection |
| T2 | **Exfil Preparation** | Behavioral shifts and technical preparation before data movement |
| T3 | **Exfiltration** | Active movement of organizational data outside authorized boundaries |
| T4 | **Obfuscation / Evasion** | Anti-forensics techniques to suppress or corrupt evidence |
| T5 | **Privilege Abuse** | Exploitation of legitimate access rights beyond authorized scope |
| T6 | **Behavioral Correlation** | The core detection layer — multi-signal analysis against baselines |
| T7 | **Decision & Escalation** | Governance controls for evidence-based case creation and HR involvement |

### Example Techniques

| Technique ID | Name | Tactic | Detections |
|---|---|---|---|
| T1.1 | Bulk data access | Collection | DT045, DT047, DT094, DT101, DT102 |
| T3.3 | Removable media transfer | Exfiltration | DT020, DT021, DT022, DT023, DT099 |
| T4.2 | Timestomping | Obfuscation / Evasion | DT013, DT091, DT092, DT109, DT156 |
| T4.1 | Log deletion and clearing | Obfuscation / Evasion | DT001, DT002, DT003, DT004, DT014 |
| T6.1 | Multi-signal correlation | Behavioral Correlation | DT045, DT047, DT101, DT102 |
| T2.4 | Unauthorized remote access setup | Exfil Preparation | DT119, DT120, DT121, DT122 |

---

## 🔍 Features

- **Matrix view** — Classic ATT&CK-style grid with tactic columns and technique cells
- **Heatmap view** — Color-coded by detection coverage so gaps are instantly visible
- **Tactic filters** — Isolate any single tactic column with one click
- **Search** — Filter by technique name or detection ID (e.g. `DT021`, `timestomp`)
- **Detail panels** — Click any technique to see full description and all mapped detection IDs
- **Stats bar** — Live counts of tactics, techniques, detection IDs, and coverage percentage
- **Zero dependencies** — Pure HTML/CSS/JS, works fully offline

---

## 🗺️ Detection ID Reference

Detection mappings follow the `DT###` numbering convention. Each detection ID maps to a specific artifact, log source, tooling capability, or investigative method. Examples:

| ID | Detection |
|----|-----------|
| DT001 | ConsoleHost_history.txt Created Timestamp Discrepancy |
| DT021 | USBSTOR Registry Key |
| DT048 | Data Loss Prevention Solution |
| DT094 | Microsoft Unified Audit Log |
| DT110 | MIP Label Activity Monitoring |
| DT137 | Physical Access vs System Auth Discrepancy |
| DT146 | File Integrity Monitoring |
| DT153 | Watermark-Based Attribution |

Click any technique cell in the matrix to see all mapped detections with full descriptions.

---

## 🆚 How This Differs from MITRE ATT&CK

| | MITRE ATT&CK® | This Framework |
|---|---|---|
| **Threat actor** | External adversaries | Malicious or negligent insiders |
| **Detection focus** | Action-based (what tool/technique) | Behavior-based (deviation from baseline) |
| **Governance layer** | Not included | First-class tactic (T7) |
| **Context validation** | Not included | Built in (T6.3) |
| **Signal model** | Single indicator can trigger | Multiple independent signals required |
| **Escalation gates** | Not modeled | Explicit case creation thresholds |

The key design principle: **a score is not intent**. No single signal is actionable on its own. Escalation requires corroborated, multi-source signals with no valid business explanation.

---

## 🔧 Customization

The matrix data lives in a single JavaScript object inside `insider-threat-matrix.html`. To add or edit techniques and detections:

1. Open the file in any text editor
2. Find the `MATRIX` array (search for `const MATRIX=`)
3. Add a new technique object inside the relevant tactic:

```javascript
{
  id: 'T1.8',
  name: 'Your technique name',
  desc: 'Description of what this technique involves.',
  dts: ['DT045', 'DT101']   // Detection IDs that cover this technique
}
```

4. To add a new detection, find the `DT` object (search for `const DT=`) and add:

```javascript
DT999: {
  name: 'Your Detection Name',
  desc: 'What this detection captures and how it works.'
}
```

---

## 📚 References

- [MITRE ATT&CK®](https://attack.mitre.org) — The adversary tactics and techniques framework this is modeled after
- [Insider Threat Matrix™](https://www.insiderthreatmatrix.org) — Detection ID reference source (Forscie Limited)
- [MITRE ATLAS](https://atlas.mitre.org) — AI-focused threat matrix (related reference)
- [CERT Insider Threat Center](https://www.sei.cmu.edu/our-work/insider-threats/) — Research and case studies

---

## 📄 License

MIT License — use, modify, and distribute freely. Attribution appreciated but not required.

---

<p align="center">
  Built for defenders. Structured for operators. Governed for investigators.
</p>
