# Modul 04 — Agentic AI: Mentransformasi Customer Journey End-to-End

**Tahap:** 4 — Desain Agentic AI
**Peserta:** process owner, tim CX, tim transformasi, AI/automation engineer (n8n)

## Tujuan

Menggunakan pendekatan dekomposisi **journey → proses → workflow → task** untuk
menemukan peluang AI agent terbesar dan menyusun business case di level task.

## Latar Belakang

Menurut McKinsey, agentic AI dapat melakukan lebih dari sekadar proses
*plug-and-play*: AI agent bisa mentransformasi seluruh pengalaman. **Peluang
terbesar untuk AI agent ada di level workflow**, karena workflow menggambarkan
bagaimana pekerjaan sebenarnya dilakukan di dalam setiap proses. Ini sejalan
dengan level **Reshape** pada BCG Deploy–Reshape–Invent (Modul 01).

---

## 1. Empat Langkah Dekomposisi

```
Customer journey ──► Process breakdown ──► Workflows per proses ──► Tasks
   (1 journey)          (mis. 3–6 proses)     (2–5 per proses)       (3–10 per workflow)
                                              ▲
                                    PELUANG TERBESAR AI AGENT
```

| Langkah | Aktivitas | Output |
|---------|-----------|--------|
| **1. Customer journey mapping** | Petakan journey dari interaksi pertama hingga penyelesaian masalah. Identifikasi dan prioritaskan *moments that matter*. | Journey map + pain points + moments that matter |
| **2. Process breakdown** | Pecah setiap momen menjadi proses (mis. persetujuan refund, notifikasi pelanggan). Satu proses biasanya terdiri dari beberapa workflow. | Daftar proses per momen |
| **3. Workflow automation** | Otomasi lintas beberapa workflow agar AI agent bisa di-scale melampaui use case terisolasi. | Desain workflow agentic (to-be) |
| **4. Task-level business case** | Nilai business case AI agent di level task untuk menghitung kelayakan dan kompleksitas deployment. | Skor task + business case |

---

## 2. Contoh: Journey "Komplain dan Refund Pelanggan"

| Momen | Proses | Workflow | Task (contoh) | Kandidat agent? |
|-------|--------|----------|---------------|-----------------|
| Pelanggan komplain | Intake komplain | Klasifikasi & routing | Baca pesan, deteksi intent, ekstrak no. order, tentukan prioritas | ✅ Tinggi |
| | | Verifikasi pelanggan | Cocokkan identitas, cek riwayat | ✅ (dengan kontrol PII) |
| Investigasi | Validasi klaim | Cek data transaksi | Query ERP/OMS, cek status pengiriman | ✅ Tinggi |
| | | Penilaian kebijakan | Bandingkan klaim dengan kebijakan refund | ✅ Sedang (human review di atas threshold) |
| Penyelesaian | Persetujuan refund | Approval | Auto-approve < Rp X; eskalasi > Rp X | ⚠️ Human-in-the-loop |
| | | Eksekusi pembayaran | Buat instruksi refund di sistem keuangan | ⚠️ Kontrol ketat |
| Notifikasi | Komunikasi pelanggan | Notifikasi status | Susun dan kirim pesan personal | ✅ Tinggi |
| Pembelajaran | Analisis akar masalah | Analisis tren komplain | Kluster komplain, laporan mingguan | ✅ Tinggi |

**Implementasi workflow:** orkestrasi dapat dibangun dengan **n8n** (trigger → AI
agent node → tool/API call → human approval node → notifikasi), terhubung ke AI
gateway dan guardrails (Modul 03).

---

## 3. Task-Level Scoring

Nilai setiap task (skala 1–5):

| Kriteria | Pertanyaan | 1 | 5 |
|----------|------------|---|---|
| **Volume** | Seberapa sering task terjadi? | Jarang | Ribuan/bulan |
| **Effort manual** | Berapa waktu/biaya per eksekusi? | < 1 menit | > 30 menit |
| **Rule-ability / pola** | Seberapa terstruktur logikanya? | Sangat bergantung judgment | Pola jelas |
| **Ketersediaan data & API** | Apakah data/sistem bisa diakses agent? | Tidak ada API | API dan data siap |
| **Risiko kesalahan** (dibalik) | Dampak jika agent salah? | Fatal/regulasi | Mudah dikoreksi |
| **Dampak pelanggan** | Pengaruh ke kepuasan/NPS? | Minim | Sangat besar |

**Agent Opportunity Score** = rata-rata (Volume, Effort, Dampak) × rata-rata (Pola, Data, Risiko⁻¹)

- **Value** = Volume, Effort, Dampak pelanggan
- **Feasibility** = Pola, Data & API, Risiko (dibalik)

| | Feasibility rendah | Feasibility tinggi |
|---|---|---|
| **Value tinggi** | 🔶 Strategic bet: bangun fondasi dulu | 🟢 **Prioritas utama** |
| **Value rendah** | ⛔ Tunda | 🔵 Quick win / otomasi sederhana |

---

## 4. Business Case per Task/Workflow

| Komponen | Rumus / sumber |
|----------|----------------|
| Penghematan biaya | Volume × waktu per task × % otomasi × biaya per jam |
| Peningkatan pendapatan/retensi | Δ konversi / Δ churn × nilai pelanggan |
| Peningkatan kualitas | Δ error rate × biaya per error |
| Biaya AI | Biaya model (token) + platform + integrasi + pemeliharaan (FinOps, Modul 03) |
| Biaya perubahan | Pelatihan, redesign proses, change management (ingat 70% di 10-20-70) |
| **ROI** | (Manfaat − Biaya) / Biaya, dihitung per tahun |
| **Payback** | Investasi awal / manfaat bersih bulanan |

## 5. Level Otonomi AI Agent

| Level | Deskripsi | Kapan dipakai |
|-------|-----------|---------------|
| L1: Assist | Agent memberi saran, manusia memutuskan dan mengeksekusi | Risiko tinggi, tahap awal |
| L2: Act with approval | Agent menyiapkan aksi, manusia menyetujui | Transaksi bernilai |
| L3: Act & notify | Agent mengeksekusi, manusia dapat membatalkan | Risiko sedang, volume tinggi |
| L4: Autonomous | Agent mengeksekusi penuh dalam batas yang ditetapkan | Risiko rendah, terbukti stabil |

Naikkan level otonomi **secara bertahap** berdasarkan bukti metrik kualitas (Modul 05).

## 6. Checklist Keluar Tahap 4

- [ ] Journey map dengan moments that matter
- [ ] Dekomposisi proses → workflow → task
- [ ] Skor Agent Opportunity untuk setiap task
- [ ] Business case untuk 3–5 workflow prioritas
- [ ] Level otonomi dan titik human-in-the-loop ditetapkan
- [ ] Risk tier (NIST, Modul 01) dan kontrol untuk setiap workflow
