# Modul 03 — Arsitektur Referensi Gen AI

**Tahap:** 3 — Arsitektur
**Peserta:** CIO/CTO, IT architect, data lead, risk/security

## Tujuan

Memahami komponen platform yang dibutuhkan agar gen AI bisa di-scale secara
**aman, dapat dipakai ulang, dan terukur**, serta menilai kematangan platform saat ini.

## Latar Belakang

McKinsey mengamati bahwa perusahaan yang men-deploy gen AI secara luas cenderung
mengikuti **arsitektur referensi yang serupa**. Arsitektur ini memiliki empat
blok utama (A–D) yang mengelilingi *shared data platform* dan *solution/use case*,
serta terhubung ke sistem IT perusahaan dan penyedia model.

---

## 1. Peta Arsitektur

```
 ┌─────────────── Sistem IT perusahaan (ERP, ITSM, HRIS, Payroll, CRM) ───────────────┐
 │                         ▲ data                 ▲ API                                │
┌┴──────────────┐  ┌──────┴──────────────┐  ┌──────┴──────────────────┐  ┌────────────┴─────┐
│ A. PLATFORM   │  │ SHARED DATA PLATFORM│  │ SOLUTION / USE CASE     │  │ PENYEDIA MODEL   │
│    PORTAL     │  │ Data terstruktur &  │  │ UI · business logic ·API│  │ Cloud foundation │
│ Katalog solusi│  │ tidak terstruktur → │1:n│ Prompt eng · LLM orch.  │  │ models (+fine-   │
│ Portofolio    │  │ tagging → kualitas →│──►│ Intent/attribution agent│  │ tuning)          │
│ POC/MVP/PROD  │  │ embeddings → vector │  │ Data tier (DB, storage) │  │ Data science:    │
│ Dokumentasi   │  │ DB → cache & API    │  └─────────────────────────┘  │ model internal   │
└───────────────┘  │ Data controls       │                               └──────────────────┘
                   └─────────────────────┘
┌──────────────────────────────────┐ ┌──────────────────────────────────────────────────┐
│ B. COMPLIANCE & AUTOMATION       │ │ C. SHARED SERVICES                               │
│ Code mgmt → CI/CD → control gates│ │ AI gateway · guardrails otomatis · prompt library│
│ → stage gate approvals           │ │ feedback service · LLM audit database            │
└──────────────────────────────────┘ └──────────────────────────────────────────────────┘
┌──────────────────────────────────────────────────────────────────────────────────────┐
│ D. GOVERNANCE & GUARDRAILS: private data mgmt · security · solution life cycle ·      │
│    responsible AI (bias) · hallucination audit · FinOps · foundation model governance │
│    + analytics, logging, monitoring                                                   │
└──────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 2. Penjelasan Blok

### A. Gen AI Platform Portal: satu "pane of glass"
Satu tempat bagi pemangku kepentingan untuk memantau, mengelola, dan berinteraksi
dengan aplikasi gen AI.
- **Solution catalog (marketplace):** chatbot, virtual expert, Q&A dokumen; component library; provisioning/deprovisioning.
- **Active portfolio:** status setiap solusi (**POC → MVP → PROD**), lengkap dengan metrik, dokumen, dan tautan.
- **Dokumentasi:** operasi platform, pembelajaran gen AI, panduan pengembangan solusi.

### B. Gen AI Solution Automation (static compliance & automation)
Infrastruktur cloud dan pola deployment yang mengotomasi pembuatan resource yang
aman dan sesuai kebijakan (DevSecOps).
- Code management, lalu **CI/CD pipeline** dengan **automated control gates**, lalu **stage gate approvals**.

### C. Gen AI Shared Services
Layanan bersama yang dipakai semua solusi untuk memastikan operasi yang bertanggung jawab.
- **AI gateway service:** satu pintu akses ke semua model (routing, rate limit, kontrol biaya, logging).
- **Automated guardrails:** filter konten, deteksi data pribadi (PII), perlindungan dari prompt injection.
- **Prompt library:** prompt standar yang ter-versioning.
- **Feedback service:** umpan balik pengguna (👍/👎, koreksi).
- **LLM audit database:** jejak audit seluruh interaksi.

### D. Gen AI Governance & Guardrails
Kerangka kontrol yang memberi manusia kendali penuh atas otomasi dan kepatuhan kebijakan.
- Private data management, security, solution life cycle, use case onboarding.
- **Responsible AI** (bias etis), **hallucination audit**, **FinOps**, **foundation model governance**.
- Analytics, logging, dan monitoring lintas platform.

### Shared Data Platform
Data terstruktur dan tidak terstruktur diproses lewat data prep (tagging dan kualitas),
dibuat embeddings, disimpan di vector database, lalu disajikan via cache dan API.
Seluruh alur dilindungi **data controls**. Satu platform data melayani banyak
use case (relasi 1:n).

### Penyedia Model
- **Cloud foundation models** (mis. layanan model terkelola dari cloud provider dan penyedia LLM), dengan opsi fine-tuning.
- **Model internal** yang dikembangkan tim data science (analyze, train, deploy) untuk kebutuhan khusus atau data sangat sensitif.
- **Prinsip:** arsitektur **multi-model dan model-agnostic** melalui AI gateway, sehingga model dapat diganti tanpa membangun ulang solusi.

---

## 3. Platform Maturity Checklist

Skor setiap komponen: **0** = belum ada, **1** = parsial/manual, **2** = ada dan terotomasi.

| Blok | Komponen | Skor (0–2) |
|------|----------|------------|
| A | Katalog solusi & component library | |
| A | Portofolio dengan status POC/MVP/PROD dan metrik | |
| A | Dokumentasi platform & panduan developer | |
| B | CI/CD dengan automated control gates | |
| B | Stage gate approval terintegrasi | |
| C | AI gateway (routing multi-model, rate limit, logging) | |
| C | Guardrails otomatis (PII, toxicity, prompt injection) | |
| C | Prompt library ter-versioning | |
| C | Feedback service | |
| C | LLM audit database | |
| D | Private data management & klasifikasi data | |
| D | Responsible AI / bias testing | |
| D | Hallucination audit / evaluasi kualitas | |
| D | FinOps (biaya per use case, per pengguna, per token) | |
| D | Foundation model governance (persetujuan model) | |
| Data | Pipeline embeddings & vector DB bersama | |
| Data | Data quality & data controls | |
| Integrasi | API ke sistem inti (ERP, CRM, HRIS, ITSM) | |
| **Total** | | **/ 36** |

**Interpretasi:** 0–12 = fondasi; 13–24 = siap pilot terkontrol; 25–36 = siap scaling.

## 4. Prinsip Desain

1. **Bangun sekali, pakai ulang berkali-kali:** shared services dan data platform melayani banyak use case.
2. **Governance by design:** kontrol diotomasi di pipeline, bukan dicek manual di akhir.
3. **Model-agnostic:** hindari lock-in; evaluasi model secara berkala.
4. **Observability:** semua interaksi tercatat untuk audit, evaluasi, dan FinOps.
5. **Privacy by design:** data pribadi dimasking/dianonimkan sebelum dikirim ke model eksternal (UU PDP).

## 5. Keterkaitan

- Skor platform menjadi bagian dari dimensi **Technology** dan **Data** (Modul 01 F5, Modul 05).
- Status POC/MVP/PROD di portal adalah basis **stage gate** di Modul 05.
- Feedback service, audit DB, dan FinOps adalah **sumber data** untuk KPI di Modul 05.
