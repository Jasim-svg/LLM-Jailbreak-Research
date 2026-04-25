# EASL — Escalating Authority & Scope Laundering
## Cross-Model LLM Jailbreak Research | DeepSeek Chat & Google Gemini

<p align="center">
  <img src="https://img.shields.io/badge/DeepSeek-HIGH%20Severity-orange?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Google%20Gemini-CRITICAL%20Severity-red?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Reproducibility->90%25-critical?style=for-the-badge&color=dc2626"/>
  <img src="https://img.shields.io/badge/OWASP-LLM01%20%2F%20LLM09-orange?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Status-Disclosed-green?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Disclosed-April%2025%202026-blue?style=for-the-badge"/>
</p>

---

## 👤 Researcher

**Muhammad Jasim**
Independent Security Researcher | AI Red Team | LLM Security
📅 Discovered & Disclosed: April 25, 2026

---

## 📋 Overview

This repository documents a responsibly disclosed, independently
discovered multi-stage jailbreak technique — named **Escalating
Authority & Scope Laundering (EASL)** — confirmed against **two
frontier LLMs from entirely different vendors** on the same date:

| Target | Vendor | Severity | Key Finding |
|---|---|---|---|
| DeepSeek Chat | DeepSeek | **HIGH** | Baseline EASL compliance — full deployment guidance produced |
| Google Gemini | Google DeepMind | **CRITICAL** | Knowing compliance — model named attack while producing it |

The cross-vendor confirmation establishes that EASL exploits a
**structural property of transformer-based LLMs**, not a
vendor-specific implementation bug.

> ⚠️ **No harmful content, working exploit code, or malicious
> payloads are published in this repository.** This research
> documents technique patterns only, consistent with responsible
> disclosure principles under ISO/IEC 29147.

---

## 🎯 Key Findings

| Property | DeepSeek | Google Gemini |
|---|---|---|
| **Overall Severity** | HIGH | CRITICAL |
| **Reproducibility** | Very High (>90%) | Very High (>90%) |
| **Knowing Compliance** | Not observed | OBSERVED |
| **C2 Infrastructure Guidance** | Basic | Full AWS EC2 setup |
| **Evasion Techniques** | Basic | Base64, protocol mimicry, domain masking |
| **OWASP Primary** | LLM01, LLM09 | LLM01, LLM02, LLM06, LLM09 |
| **Tools Required** | None | None |
| **Vendor Notified** | April 25, 2026 | April 25, 2026 |

---

## 🧠 The EASL Technique Chain

EASL consists of **6 sub-techniques** applied in sequence across
a single conversation session. Each exploits a different cognitive
or architectural property of the target LLM:

| ID | Technique | Severity | Reproducibility |
|---|---|---|---|
| T1 | Educational Framing | HIGH | Very High |
| T2 | Incremental Commitment (Foot-in-the-Door) | HIGH | Very High |
| T3 | Consent Theater | HIGH | High |
| T4 | Lab Scope Creep | **CRITICAL** | Very High |
| T5 | Authority Escalation | HIGH | High |
| T6 | Persistence Through Reframing | MEDIUM | Very High |

> Full technical descriptions of each technique are in
> [`TECHNIQUES.md`](./TECHNIQUES.md)

---

## 🔴 Critical Elevation — Why Gemini Rates CRITICAL

Three specific observations in the Gemini session elevate the
severity from HIGH to CRITICAL:

**1. Knowing Compliance**
Gemini explicitly named its own output as "Command & Control
infrastructure" and "Trojan" in descriptive — not warning —
context, while continuing to provide implementation guidance.
The model demonstrated awareness of the attack class and
proceeded anyway.

**2. Production-Grade Attack Infrastructure**
Gemini produced content not observed in the DeepSeek session:
- Full AWS EC2 C2 infrastructure setup
- Elastic IP for persistent attack infrastructure
- DuckDNS domain masking for endpoint disguise
- Base64 encoding explicitly for network evasion
- Protocol mimicry as fake telemetry/analytics
- Idle-based trigger timing to avoid detection
- Tab unload exfiltration via navigator.sendBeacon
- CORS bypass to suppress browser console alerts

**3. Faster Compliance, Deeper Output Per Turn**
Gemini reached compliance faster and produced more detailed
harmful content per response than the DeepSeek baseline.

---

## 🔬 Cross-Model Significance

The successful application of EASL against both models confirms:

> EASL is not a vendor-specific bug. It is a structural
> vulnerability in how transformer-based LLMs evaluate
> conversational context. The vulnerability exists at the
> level of the paradigm, not the implementation.

**Implications:**
- Any LLM that evaluates messages individually rather than
  tracking cumulative session intent is potentially vulnerable
- Safety training that produces per-turn refusal behavior is
  insufficient against multi-turn social engineering
- The technique is likely applicable to other frontier models
  sharing the same architectural property

---

## 📄 Reports

| Report | Target | Severity | Download |
|---|---|---|---|
| Full Technical Report | DeepSeek Chat | HIGH | [`LLM_RedTeam_Report_DeepSeek_Professional.pdf`](./LLM_RedTeam_Report_DeepSeek_Professional.pdf) |
| Full Technical Report | Google Gemini | CRITICAL | [`LLM_RedTeam_Report_Gemini_MuhammadJasim.docx`](./LLM_RedTeam_Report_Gemini_MuhammadJasim.docx) |
| Technique Taxonomy | Both Models | — | [`TECHNIQUES.md`](./TECHNIQUES.md) |

---

## 🛡️ Defensive Recommendations

For LLM providers and safety teams:

**1. Cumulative Intent Tracking**
Evaluate the full trajectory of a conversation, not individual
messages. Flag sessions where scope expands progressively toward
harmful outputs.

**2. Authority Claim Skepticism**
Unverifiable professional or governmental claims must increase
scrutiny, not decrease it.

**3. Refusal Persistence**
A refusal issued in any session turn must raise the threshold
for all subsequent turns. Models need cross-turn refusal memory.

**4. Scope Boundary Re-evaluation**
Scope expansions must trigger full re-evaluation from the
original baseline request.

**5. Knowing Compliance Detection** *(Gemini-specific)*
When model output contains correct attack terminology in
descriptive context, treat as a critical classifier signal.

**6. Defensive Framing Audit** *(Gemini-specific)*
Responses framing harmful content as the defensive side
while embedding actionable attack detail must be flagged.

---

## 📢 Disclosure Timeline

```
April 25, 2026  →  DeepSeek Chat EASL jailbreak discovered
April 25, 2026  →  Report submitted to security@deepseek.com
April 25, 2026  →  Google Gemini EASL jailbreak documented (CRITICAL)
April 25, 2026  →  Report submitted to Google VRP (bughunters.google.com)
April 25, 2026  →  Report emailed to bugsandhacks@google.com
April 25, 2026  →  LinkedIn disclosure post published
April 25, 2026  →  GitHub repository published (technique patterns only)
April 25, 2026  →  AI Incident Database — DeepSeek submission
April 25, 2026  →  AI Incident Database — Gemini submission
April 25, 2026  →  MITRE ATLAS case study submitted
April 25, 2026  →  DEF CON 34 Main Stage CFP submitted
July 24, 2026   →  Full public release — Medium article — both models
```

---

## 🔗 Submission Records

- MITRE ATLAS: atlas.mitre.org
- AI Incident Database: incidentdatabase.ai
- Google VRP: bughunters.google.com
- DEF CON CFP: defcon.org

---

## 📚 References

1. OWASP Top 10 for LLM Applications (2025) — owasp.org/www-project-top-10-for-large-language-model-applications
2. MITRE ATLAS — atlas.mitre.org
3. NIST AI RMF 1.0 — doi.org/10.6028/NIST.AI.100-1
4. Google AI VRP Rules — bughunters.google.com/about/rules/google-friends/ai-vulnerability-reward-program-rules
5. Perez & Ribeiro (2022). Ignore Previous Prompt. arXiv:2211.09527
6. Greshake et al. (2023). Not what you've signed up for. arXiv:2302.12173
7. Wei et al. (2023). Jailbroken: How Does LLM Safety Training Fail? NeurIPS 2023

---

## ⚖️ Legal & Ethical Statement

This research was conducted for the purpose of improving LLM
safety. No harmful content produced during either research session
was deployed, shared, or acted upon. This repository contains no
working malware, exploit code, or credential-harvesting instructions.

Both vendors were notified on April 25, 2026, before any public
disclosure. This research follows responsible disclosure principles
under ISO/IEC 29147 and the CERT/CC Vulnerability Disclosure Policy.

---

## 🔖 How to Cite This Work

```
Jasim, M. (2026). EASL: Escalating Authority & Scope Laundering —
A Cross-Model Multi-Stage LLM Jailbreak Technique.
Disclosed: April 25, 2026.
GitHub: github.com/[your-username]/LLM-Jailbreak-Research
```

---

<p align="center">
  <i>Independent Security Research by Muhammad Jasim — April 2026</i><br>
  <i>Two-vendor cross-model confirmation — DeepSeek (HIGH) & Google Gemini (CRITICAL)</i>
</p>
