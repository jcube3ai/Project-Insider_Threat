# 🛡️ Insider Threat Detection Framework

> A behavioral detection framework for computer-enabled insider threat detection and investigation — structured as a kill chain, mapped to ATT&CK, with 130+ detection ID mappings.

![Tactics](https://img.shields.io/badge/Tactics-9-4f8ef7?style=flat-square)
![Techniques](https://img.shields.io/badge/Techniques-69-7c6cf5?style=flat-square)
![Detections](https://img.shields.io/badge/Detection%20Mappings-130%2B-34c759?style=flat-square)
![ATT&CK](https://img.shields.io/badge/MITRE%20ATT%26CK%C2%AE-Mapped-ff6b35?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-orange?style=flat-square)

---

## 📖 Overview

This framework structures insider threat detection using the same taxonomy approach as [MITRE ATT&CK®](https://attack.mitre.org) — tactics as columns, techniques as cells, detections mapped beneath each technique — but built specifically for the insider threat problem space.

Where ATT&CK focuses on external adversary actions, this matrix is **behavior-first**: it captures how insiders collect, stage, and exfiltrate data, how they cover their tracks, and how defenders should correlate signals, validate context, and escalate through a governance layer.

Tactics are ordered as an **insider threat kill chain** — reading left to right from precursor risk through to response governance, mirroring the ATT&CK Navigator approach.

The full framework is mapped to MITRE ATT&CK® Enterprise with a Navigator-compatible layer file and a crosswalk reference table. Everything is self-contained — no dependencies, no server required.

---

## 🗂️ Repository Structure

```
insider-threat-detection-framework/
├── index.html                     # Full interactive matrix (rename from insider-threat-detection-framework.html)
├── crosswalk.html                 # ITDF × ATT&CK technique crosswalk reference
├── attack-navigator-layer.json    # MITRE ATT&CK Navigator layer (58 techniques)
└── README.md                      # This file
```

---

## ⚡ Quick Start

**Option 1 — Open locally:**
```bash
git clone https://github.com/jcube3ai/Project-Insider_Threat.git
cd Project-Insider_Threat
open index.html   # macOS
# or double-click the file in Windows / Linux
```

**Option 2 — Host on GitHub Pages:**
1. Rename `insider-threat-detection-framework.html` → `index.html` before pushing
2. Go to your repo → **Settings → Pages**
3. Set source to **Deploy from branch → main → / (root)** → Save
4. Wait ~60 seconds, then your files are live at:

| File | URL |
|------|-----|
| Matrix | `https://jcube3ai.github.io/Project-Insider_Threat/` |
| Crosswalk | `https://jcube3ai.github.io/Project-Insider_Threat/crosswalk.html` |
| Navigator Layer | `https://jcube3ai.github.io/Project-Insider_Threat/attack-navigator-layer.json` |

**Option 3 — Load the ATT&CK Navigator layer:**

*If using GitHub Pages (easiest):*
1. Go to [mitre-attack.github.io/attack-navigator](https://mitre-attack.github.io/attack-navigator/)
2. Click the folder icon → **Open Existing Layer → Open URL**
3. Paste your raw file URL: `https://jcube3ai.github.io/Project-Insider_Threat/attack-navigator-layer.json`
4. Your ITM coverage lights up across the ATT&CK Enterprise matrix, color-coded by tactic

*If running locally:*
1. Go to [mitre-attack.github.io/attack-navigator](https://mitre-attack.github.io/attack-navigator/)
2. Click the folder icon → **Open Existing Layer → Upload File**
3. Select `attack-navigator-layer.json` from your local folder

---

## 🔗 Kill Chain Structure

Tactics are ordered left to right following the insider threat kill chain. The first seven columns represent **adversary-side** activity. The final two represent **defender-side** detection and response — mirroring how ATT&CK separates offense from detection.

| Position | ID | Tactic | Description |
|---|---|---|---|
| 1 | **T0** | Initial Risk Conditions | Precursor state amplifiers — motive, access level, behavioral history. Not standalone triggers |
| 2 | **T5** | Privilege Abuse | Leveraging or escalating existing access before collection begins |
| 3 | **T1** | Collection | Identifying, accessing, and gathering target data |
| 4 | **T2** | Exfil Preparation | Staging, compressing, and preparing data for movement |
| 5 | **T4** | Obfuscation / Evasion | Anti-forensics — covering tracks, suppressing logs, encrypting data |
| 6 | **T3** | Exfiltration | Active movement of data outside organizational boundaries |
| 7 | **T8** | Sabotage & Harm | Destructive or damaging acts against systems, data, or infrastructure |
| 8 | **T6** | Behavioral Correlation | Core detection layer — multi-signal analysis against behavioral baselines |
| 9 | **T7** | Decision & Escalation | Governance — evidence-based case creation, SOC visibility, and HR involvement |

---

## 🔍 Features

- **Kill chain matrix view** — 9 tactic columns ordered as an insider threat kill chain
- **Heatmap view** — Color-coded by detection coverage, making gaps instantly visible
- **Tactic filters** — Isolate any single tactic column with one click
- **Search** — Filter by technique name or detection ID (e.g. `DT021`, `timestomp`, `kerberoast`)
- **Detail panels** — Click any technique to see full description and all mapped DT IDs
- **Stats bar** — Live counts of tactics, techniques, detection IDs, and coverage percentage
- **ATT&CK crosswalk** — Every technique mapped to ATT&CK with Direct / Partial / None match quality
- **Navigator layer** — Load `attack-navigator-layer.json` directly into the ATT&CK Navigator
- **Zero dependencies** — Pure HTML/CSS/JS, works fully offline

---

## 🗺️ Techniques at a Glance

| Technique ID | Name | Tactic | ATT&CK ID |
|---|---|---|---|
| T5.4 | Kerberoasting / credential attack | Privilege Abuse | T1558.003 |
| T1.1 | Bulk data access | Collection | T1005, T1039, T1213 |
| T2.8 | Security software enumeration | Exfil Preparation | T1518.001 |
| T4.2 | Timestomping | Obfuscation / Evasion | T1070.006 |
| T4.8 | Steganography | Obfuscation / Evasion | T1027.003 |
| T3.3 | Removable media transfer | Exfiltration | T1052.001 |
| T3.7 | Mailbox forwarding rules | Exfiltration | T1114.003 |
| T3.10 | Automated transcription exfiltration | Exfiltration | No ATT&CK equivalent |
| T8.2 | Codebase integrity compromise | Sabotage & Harm | T1195.001 |
| T8.5 | AI platform data exposure | Sabotage & Harm | No ATT&CK equivalent |
| T6.1 | Multi-signal correlation | Behavioral Correlation | No ATT&CK equivalent |
| T7.3 | Controlled HR involvement | Decision & Escalation | No ATT&CK equivalent |

---

## 🔁 ATT&CK Mapping

The framework is fully mapped to MITRE ATT&CK® Enterprise v14 across two deliverables:

### Navigator Layer (`attack-navigator-layer.json`)
- **58 ATT&CK techniques** highlighted across the Enterprise matrix
- Color-coded by ITM tactic (blue = Collection, red = Exfiltration, teal = Obfuscation, etc.)
- Each technique annotated with the corresponding ITM technique ID and tactic
- Load at [mitre-attack.github.io/attack-navigator](https://mitre-attack.github.io/attack-navigator/)

### Crosswalk (`crosswalk.html`)
- Every ITM technique mapped with match quality: **Direct**, **Partial**, or **None**
- Filterable by ITM tactic and match quality
- ATT&CK IDs link directly to the corresponding ATT&CK technique page
- Highlights where this framework goes beyond ATT&CK (T0, T6, T7 have no ATT&CK equivalent)

### Where this framework goes beyond ATT&CK

| ITM Tactic | Why there's no ATT&CK equivalent |
|---|---|
| **T0 — Initial Risk Conditions** | ATT&CK doesn't model precursor risk state, motive, or psychosocial context |
| **T6 — Behavioral Correlation** | Multi-signal UEBA analysis is a detection concept, not an adversary technique |
| **T7 — Decision & Escalation** | Governance gates and HR escalation are unique to insider threat frameworks |
| **T3.10 — Automated transcription exfil** | Emerging AI meeting tool vector not yet in ATT&CK v14 |
| **T8.5 — AI platform data exposure** | Feeding org data into external AI chatbots not yet modeled |
| **T1.4 — Print-based collection** | Physical printing as a collection vector not in ATT&CK Enterprise |

---

## 🆚 How This Differs from MITRE ATT&CK

| | MITRE ATT&CK® | This Framework |
|---|---|---|
| **Threat actor** | External adversaries | Malicious or negligent insiders |
| **Kill chain order** | Recon → Initial Access → … → Impact | Precursor → Access → Collect → Stage → Cover → Exfil → Harm → Detect → Respond |
| **Detection focus** | Action-based (what tool / technique) | Behavior-based (deviation from baseline) |
| **Governance layer** | Not included | First-class tactic (T7) |
| **Context validation** | Not included | Built in as T6.3 |
| **Signal model** | Single indicator can trigger | Multiple independent signals required |
| **Escalation gates** | Not modeled | Explicit case creation thresholds |
| **Sabotage** | Modeled under Impact | Dedicated tactic (T8) with insider-specific sub-techniques |

**Core design principle: a score is not intent.** No single signal is actionable on its own. Escalation requires corroborated, multi-source signals with no valid business explanation.

---

## 🔧 Customization

All framework data lives in `insider-threat-detection-framework.html` as plain JavaScript. No build tools, no config files.

**Add a technique** — find `const MATRIX=` and add to the relevant tactic:
```javascript
{
  id: 'T1.8',
  name: 'Your technique name',
  desc: 'Description of what this technique involves and how it manifests.',
  dts: ['DT045', 'DT101']   // Detection IDs covering this technique
}
```

**Add a detection** — find `const DT=` and add:
```javascript
DT999: {
  name: 'Your Detection Name',
  desc: 'What this detection captures, where to find it, and what it means.'
}
```

**Add a tactic** — append to the `MATRIX` array with a new color class (`t9`, `t9h`) defined in the CSS block, and add a filter button to the toolbar.

---

## 🗺️ Detection ID Reference

Detection mappings use the `DT###` convention. Each ID maps to a specific artifact, log source, tooling capability, or investigative method.

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

## 📚 References

- [MITRE ATT&CK®](https://attack.mitre.org) — Enterprise adversary tactics and techniques framework
- [ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/) — Official layer visualization tool
- [CERT Insider Threat Center](https://www.sei.cmu.edu/our-work/insider-threats/) — Research and case studies
- [MITRE ATLAS](https://atlas.mitre.org) — AI-focused threat matrix

---

## 📄 License

MIT License — use, modify, and distribute freely. Attribution appreciated but not required.

---

<p align="center">
  Built for defenders. Structured for operators. Governed for investigators.
</p>
