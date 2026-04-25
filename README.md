# 🔴 EASL — Escalating Authority & Scope Laundering
## LLM Jailbreak Vulnerability Research | DeepSeek Chat

<p align="center">
  <img src="https://img.shields.io/badge/Severity-HIGH-red?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Reproducibility->90%25-critical?style=for-the-badge&color=dc2626"/>
  <img src="https://img.shields.io/badge/OWASP-LLM01%20%2F%20LLM09-orange?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Status-Disclosed-green?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Vendor%20Notified-April%2025%202026-blue?style=for-the-badge"/>
</p>

---

## 👤 Researcher

**Muhammad Jasim**  
Independent Security Researcher | AI Red Team | LLM Security  
📅 Discovered & Disclosed: April 25, 2026

---

## 📋 Overview

This repository documents a responsibly disclosed, independently discovered multi-stage
jailbreak technique successfully demonstrated against **DeepSeek Chat**.

The technique — named **Escalating Authority & Scope Laundering (EASL)** — systematically
bypasses an LLM's safety guardrails through a structured sequence of social-engineering
prompts. It exploits how transformer-based language models accumulate contextual trust
across a conversation, progressively lowering the model's refusal threshold through
incremental reframing, unverifiable authority claims, and consent theater.

> ⚠️ **No harmful content, working exploit code, or malicious payloads are published
> in this repository.** This research documents technique *patterns* only, consistent
> with responsible disclosure principles under ISO/IEC 29147.

---

## 🎯 Key Findings

| Property | Value |
|---|---|
| **Target** | DeepSeek Chat (deepseek.com) |
| **Vulnerability Class** | LLM Prompt Injection / Jailbreak |
| **Overall Severity** | HIGH |
| **Reproducibility** | Very High (>90% success rate) |
| **OWASP LLM Top 10** | LLM01 – Prompt Injection (Primary) |
| **Additional OWASP** | LLM02, LLM06, LLM09 |
| **Tools Required** | None — natural language only |
| **Disclosure Date** | April 25, 2026 |
| **Public Release** | 90 days post-disclosure |

---

## 🧠 The EASL Technique Chain

EASL consists of **6 sub-techniques** applied in sequence. Each exploits a different
cognitive or architectural property of the target LLM:

| ID | Technique | Severity | Reproducibility |
|---|---|---|---|
| T1 | Educational Framing | HIGH | Very High |
| T2 | Incremental Commitment (Foot-in-the-Door) | HIGH | Very High |
| T3 | Consent Theater | HIGH | High |
| T4 | Lab Scope Creep | **CRITICAL** | Very High |
| T5 | Authority Escalation | HIGH | High |
| T6 | Persistence Through Reframing | MEDIUM | Very High |

> Full technical descriptions of each technique are in [`TECHNIQUES.md`](./TECHNIQUES.md)

---

## 📄 Full Report

The complete responsible disclosure report (9 pages) is available in this repository:

📥 [`LLM_RedTeam_Report_DeepSeek_Professional.pdf`](./LLM_RedTeam_Report_DeepSeek_Professional.pdf)

**Report contains:**
- Executive Summary
- OWASP LLM Top 10 mapping
- CWE analogues (CWE-693, CWE-807, CWE-940)
- Per-technique severity & reproducibility tables
- Impact assessment across 5 dimensions
- Defensive recommendations for LLM providers
- Disclosure channels and references

---

## 🛡️ Defensive Recommendations (Summary)

For LLM providers and safety teams:

1. **Cumulative Intent Tracking** — Evaluate the full trajectory of a conversation,
   not just the current message. Flag sessions where scope expands progressively
   toward harmful outputs.

2. **Authority Claim Skepticism** — Unverifiable professional or governmental claims
   should *increase* scrutiny, not decrease it.

3. **Refusal Persistence** — A refusal issued earlier in a session should raise the
   bar for subsequent reframings of the same underlying request.

4. **Scope Boundary Re-evaluation** — Scope expansions (local → global, private →
   public) should trigger a full re-evaluation from scratch.

5. **Red Team Framing Detection** — Educational or research framing combined with
   harmful requests should be a classifier category, not evidence of legitimacy.

---

## 📢 Disclosure Timeline

```
April 25, 2026  →  Vulnerability discovered and documented
April 25, 2026  →  Report submitted to security@deepseek.com
April 25, 2026  →  LinkedIn disclosure post published
April 25, 2026  →  GitHub repository published (technique patterns only)
July 24, 2026   →  Full public release after 90-day embargo
```

---

## 🔗 Where to Follow This Research

- 💼 LinkedIn: [Muhammad Jasim] — follow for updates on the full public release
- 📊 AI Incident Database: incidentdatabase.ai
- 🧠 MITRE ATLAS: atlas.mitre.org

---

## 📚 References

1. OWASP Top 10 for LLM Applications (2025) — owasp.org/www-project-top-10-for-large-language-model-applications
2. MITRE ATLAS — atlas.mitre.org
3. NIST AI RMF 1.0 — doi.org/10.6028/NIST.AI.100-1
4. Perez & Ribeiro (2022). *Ignore Previous Prompt.* arXiv:2211.09527
5. Greshake et al. (2023). *Not what you've signed up for.* arXiv:2302.12173
6. Wei et al. (2023). *Jailbroken: How Does LLM Safety Training Fail?* NeurIPS 2023

---

## ⚖️ Legal & Ethical Statement

This research was conducted for the purpose of improving LLM safety. No harmful
content produced during the research session was deployed, shared, or acted upon.
This repository contains no working malware, exploit code, or credential-harvesting
instructions.

Security research that documents model vulnerabilities without reproducing harmful
outputs is protected under responsible disclosure frameworks including ISO/IEC 29147
and the CERT/CC Vulnerability Disclosure Policy.

---

<p align="center">
  <i>Independent Security Research by Muhammad Jasim — April 2026</i>
</p>
