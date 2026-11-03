# Modul 02 — AI Readiness Assessment (Adaptasi ASPIRE)

**Tahap:** 2 — Kesiapan
**Durasi:** 2 jam (assessment) + 1–2 minggu pengumpulan data

## Tujuan

Mengukur kesiapan organisasi untuk deployment AI secara objektif dan menemukan
gap prioritas sebelum scaling.

## Latar Belakang

**ASPIRE** (BCG, matriks 2026) mengukur kesiapan AI suatu **negara** dalam enam
dimensi: **A**mbition, **S**kills, **P**olicy & regulation, **I**nvestment,
**R**esearch & innovation, **E**cosystem. Indikator yang baru ditambahkan di
matriks 2026 antara lain *overarching national AI legislation*, *domestic AI model
development*, dan *AI compute capacity*.

Modul ini **mengadaptasi** keenam dimensi tersebut ke level **organisasi/perusahaan**.
Konteks nasional ASPIRE tetap relevan sebagai faktor eksternal, misalnya
ketersediaan talenta, regulasi, dan infrastruktur cloud di Indonesia.

---

## 1. Dimensi dan Indikator Level Organisasi

| Dimensi | Indikator ASPIRE (negara) | Adaptasi indikator organisasi |
|---------|---------------------------|-------------------------------|
| **A — Ambition** | Strategi AI nasional dan revisinya; lembaga khusus AI | Strategi AI terdokumentasi dan direview ≥1×/tahun; ada AI Council/CoE dengan mandat; sponsor C-level; target nilai AI di RKAP |
| **S — Skills** | Spesialis AI per populasi; kontribusi GitHub; Kaggle Grandmasters; unduhan paket Python | % karyawan dengan literasi AI dasar; jumlah talenta AI/data per 1.000 karyawan; % karyawan pengguna aktif tools AI; program upskilling berjalan |
| **P — Policy & Regulation** | Kualitas regulasi; efektivitas governance; data governance; legislasi AI | AI Policy & acceptable use policy; data governance (data owner, klasifikasi); kepatuhan UU PDP; proses AI risk assessment (NIST) |
| **I — Investment** | Nilai AI unicorn; pendanaan AI; VC; belanja software | Anggaran AI (% dari belanja IT/pendapatan); alokasi 10-20-70; business case per use case; mekanisme pendanaan berkelanjutan |
| **R — Research & Innovation** | Paper, paten, universitas, model AI domestik, startup AI | Jumlah eksperimen/PoC per kuartal; % PoC yang lanjut ke produksi; kemitraan dengan universitas/startup; kemampuan fine-tune/membangun model sendiri |
| **E — Ecosystem** | Data center, compute AI, cloud, adopsi teknologi, broadband, listrik | Akses cloud/compute AI; platform gen AI bersama (Modul 03); integrasi API ke sistem inti (ERP, CRM, HRIS); kemitraan vendor; kualitas konektivitas |

---

## 2. Rubrik Penilaian (Skala 1–5)

| Skor | Level | Deskripsi umum |
|------|-------|----------------|
| 1 | **Awareness** | Belum ada inisiatif terstruktur; eksperimen individual |
| 2 | **Exploring** | Ada pilot/PoC terpisah; strategi belum formal |
| 3 | **Defined** | Strategi, governance, dan platform dasar ada; beberapa use case di produksi |
| 4 | **Scaling** | AI terintegrasi di beberapa domain; KPI nilai terukur; reuse platform |
| 5 | **Transforming** | AI menjadi bagian inti model bisnis dan cara kerja; inovasi berkelanjutan |

### Rubrik detail per dimensi

| Dimensi | Skor 1 | Skor 3 | Skor 5 |
|---------|--------|--------|--------|
| Ambition | Tidak ada strategi AI | Strategi ada, sponsor ditetapkan, target belum terkuantifikasi | Strategi terkuantifikasi, direview rutin, terintegrasi dengan strategi korporat |
| Skills | <10% literasi AI | 30–60% literasi AI; tim AI inti ada | >80% literasi AI; talenta AI di setiap unit bisnis |
| Policy | Tidak ada kebijakan AI | AI Policy dan risk assessment ada untuk use case berisiko tinggi | Governance NIST penuh, audit rutin, monitoring otomatis |
| Investment | Ad hoc dari anggaran unit | Anggaran AI terpusat dengan business case | Portofolio investasi AI dikelola seperti venture, dengan stage gate |
| R&I | Tidak ada eksperimen | Pipeline PoC rutin; konversi PoC→produksi >20% | Inovasi berkelanjutan; model/IP sendiri; kemitraan ekosistem |
| Ecosystem | Tidak ada platform; data silo | Platform gen AI dasar, integrasi ke 1–2 sistem inti | Platform terpadu (Modul 03), integrasi luas, multi-model |

---

## 3. Cara Melakukan Assessment

1. **Survei** ke 20–50 responden lintas level (eksekutif, manajer, IT, HR, risk).
2. **Wawancara** 8–12 pemangku kepentingan kunci.
3. **Validasi bukti:** dokumen strategi, kebijakan, anggaran, data penggunaan tools.
4. **Workshop kalibrasi:** sepakati skor akhir per dimensi.
5. **Gap analysis:** bandingkan skor saat ini dengan target 12 bulan.

## 4. Template Hasil

| Dimensi | Bobot | Skor saat ini | Target 12 bln | Gap | Prioritas inisiatif |
|---------|-------|---------------|---------------|-----|---------------------|
| Ambition | 15% | | | | |
| Skills | 20% | | | | |
| Policy & Regulation | 20% | | | | |
| Investment | 15% | | | | |
| Research & Innovation | 10% | | | | |
| Ecosystem | 20% | | | | |
| **Indeks Readiness** | 100% | **Σ(bobot×skor)** | | | |

*Bobot dapat disesuaikan. Sektor teregulasi (keuangan, kesehatan) disarankan
menaikkan bobot Policy.*

**Interpretasi indeks:**
- **< 2,0:** fokus ke fondasi (Ambition, Policy, Skills). Mulai dari use case Deploy berisiko rendah.
- **2,0–3,4:** siap pilot terstruktur dan Reshape terbatas.
- **≥ 3,5:** siap scaling dan eksplorasi Invent.

## 5. Keterkaitan dengan Modul Lain

- Skor **Ambition** dan **Investment** menjadi masukan bagi proporsi Deploy/Reshape/Invent (Modul 01).
- Skor **Ecosystem** menentukan prioritas pembangunan platform (Modul 03).
- Skor **Skills** dan **Policy** menjadi baseline untuk KPI adopsi dan governance (Modul 05).
- Ulangi assessment setiap **6 bulan** untuk mengukur kemajuan.
