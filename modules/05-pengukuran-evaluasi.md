# Modul 05 — Pengukuran & Evaluasi Deployment dan Adopsi AI

**Tahap:** 5 — Ukur & Evaluasi
**Peserta:** PMO/transformasi, value owner, IT/data, HR/L&D, risk & compliance

## Tujuan

Menyediakan sistem pengukuran terpadu untuk menjawab empat pertanyaan:
1. **Apakah AI memberi nilai?** (Value)
2. **Apakah AI benar-benar dipakai?** (Adoption)
3. **Apakah AI bekerja dengan baik?** (Performance/Quality)
4. **Apakah AI aman dan patuh?** (Risk & Governance)

Serta satu pertanyaan organisasi: **apakah kapabilitas kita meningkat?** (Readiness & Capability)

---

## 1. Kerangka Pengukuran: AI Deployment Scorecard

Scorecard menggabungkan semua framework dari modul sebelumnya:

| Pilar | Framework sumber | Pertanyaan |
|-------|------------------|------------|
| **1. Value** | BCG Deploy–Reshape–Invent; business case Modul 04 | Nilai bisnis apa yang tercipta? |
| **2. Adoption & People** | BCG 10-20-70 (70%); ADKAR; McKinsey *Adoption & Scaling* | Apakah orang memakai AI dan mengubah cara kerja? |
| **3. Performance & Quality** | Arsitektur referensi (feedback, audit, hallucination audit) | Apakah output AI akurat, cepat, dan andal? |
| **4. Risk & Governance** | NIST AI RMF (Measure & Manage) | Apakah risiko terkendali? |
| **5. Capability** | McKinsey Six Dimensions; ASPIRE (Modul 02); platform maturity (Modul 03) | Apakah fondasi organisasi menguat? |

---

## 2. Pilar 1 — Value (Nilai Bisnis)

KPI dibedakan berdasarkan jenis inisiatif:

| Jenis | KPI utama | Rumus |
|-------|-----------|-------|
| **Deploy** (produktivitas) | Jam kerja dihemat, *value-realized hours* | Σ (waktu sebelum − waktu sesudah) × volume × % jam yang dialihkan ke pekerjaan bernilai |
| **Reshape** (proses) | Cycle time, biaya per transaksi, first-time-right, NPS/CSAT | (Baseline − aktual) / baseline |
| **Invent** (bisnis baru) | Pendapatan baru, pelanggan baru, margin | Pendapatan dari produk/fitur AI |
| **Semua** | ROI, payback, cost per outcome | (Manfaat − Total biaya) / Total biaya |

**Prinsip penting:**
- Tetapkan **baseline** sebelum go-live. Tanpa baseline, nilai tidak bisa dibuktikan.
- Bedakan **nilai potensial** (jam dihemat) dari **nilai terealisasi** (biaya turun, output naik, atau kapasitas dialihkan).
- Gunakan **grup kontrol / A-B test** bila memungkinkan.
- Value owner dari bisnis, bukan IT, yang menandatangani klaim nilai.

---

## 3. Pilar 2 — Adoption & People (Porsi 70%)

### 3.1 Funnel adopsi

```
Akses ─► Terlatih ─► Mencoba ─► Aktif rutin ─► Kebiasaan ─► Redesign kerja
(licensed) (trained)  (trial)    (WAU/MAU)      (habit)      (process change)
```

| KPI | Definisi | Target indikatif |
|-----|----------|------------------|
| Coverage | % target user yang punya akses | 100% |
| Training completion | % user yang menyelesaikan pelatihan | > 90% |
| Activation rate | % user yang mencoba ≥1× dalam 30 hari | > 70% |
| **Active usage (WAU/MAU)** | % user aktif mingguan / bulanan | WAU > 50%, MAU > 70% |
| Stickiness | WAU ÷ MAU | > 0,6 |
| Depth of use | Interaksi per user per minggu; jumlah fitur/use case dipakai | Naik bulan ke bulan |
| Breadth | % unit/fungsi dengan pengguna aktif | > 80% |
| Process adoption | % transaksi proses yang melewati workflow AI | Sesuai target per use case |
| User satisfaction | CSAT/NPS internal tools AI; rasio 👍/👎 | CSAT > 4/5 |

*Target bersifat indikatif. Sesuaikan dengan baseline dan jenis use case.*

### 3.2 Indikator perubahan perilaku (ADKAR)

| Tahap ADKAR | Indikator | Cara mengukur |
|-------------|-----------|---------------|
| **Awareness** | % karyawan yang paham alasan dan tujuan AI | Pulse survey |
| **Desire** | % yang ingin memakai AI; tingkat kekhawatiran terhadap pekerjaan | Survei sentimen |
| **Knowledge** | Skor literasi AI; kelulusan pelatihan | Asesmen |
| **Ability** | % yang mampu menyelesaikan task nyata dengan AI | Observasi / tugas praktik |
| **Reinforcement** | AI masuk ke SOP, KPI individu, dan pengakuan/insentif | Audit SOP, data HR |

### 3.3 Learning agility & budaya
- Jumlah AI champion per unit (target ≥1 per 50 karyawan).
- Jumlah ide use case dari bawah (bottom-up) per kuartal.
- % pemimpin yang aktif memakai AI (leadership role modeling).

---

## 4. Pilar 3 — Performance & Quality

| Kategori | KPI | Sumber data (Modul 03) |
|----------|-----|------------------------|
| Akurasi | Accuracy / task success rate pada test set; first-contact resolution | Evaluation pipeline |
| Hallucination | % jawaban tidak berdasar (groundedness) | Hallucination audit |
| Relevansi | Rating pengguna, rasio 👍/👎 | Feedback service |
| Keandalan | Uptime, error rate, % fallback ke manusia | Monitoring |
| Kecepatan | Latensi p50/p95 | AI gateway |
| Efisiensi biaya | Biaya per interaksi / per outcome; biaya per user aktif | FinOps |
| Agentic | % task selesai end-to-end tanpa eskalasi; tingkat eskalasi yang tepat | Audit DB |
| Drift | Perubahan kualitas dari waktu ke waktu | Evaluasi berkala |

**Metode evaluasi:**
- **Golden test set** (50–500 kasus representatif) dijalankan di setiap perubahan prompt/model.
- **LLM-as-judge** untuk skala, dikalibrasi dengan **human review** sampel (mis. 5–10%).
- **Online evaluation:** feedback pengguna dan sampling percakapan produksi.

---

## 5. Pilar 4 — Risk & Governance (NIST Measure & Manage)

| KPI | Definisi |
|-----|----------|
| % use case dengan AI impact assessment | Use case di produksi yang sudah dinilai risikonya (target 100%) |
| % use case tier tinggi dengan human-in-the-loop | Target 100% |
| Insiden AI | Jumlah dan severitas insiden (kebocoran data, output berbahaya, keputusan salah) |
| MTTD / MTTR insiden AI | Waktu deteksi dan pemulihan |
| Guardrail trigger rate | % interaksi yang diblokir/dimodifikasi guardrails |
| Kebocoran PII | Jumlah deteksi data pribadi ke model eksternal (target 0) |
| Bias / fairness | Selisih performa antar kelompok (untuk use case keputusan tentang orang) |
| Kepatuhan kebijakan | % pengguna yang menyetujui acceptable use policy; temuan audit |
| Shadow AI | Penggunaan tools AI tidak resmi (dari log jaringan/CASB) |

---

## 6. Pilar 5 — Capability (Six Dimensions)

Ulangi penilaian setiap 6 bulan:

| Dimensi | Indikator | Sumber |
|---------|-----------|--------|
| Strategy | % use case dengan value owner dan target nilai | Portofolio |
| Talent | Literasi AI, jumlah talenta AI, retensi talenta AI | HR / Modul 02 Skills |
| Operating Model | Jumlah squad AI aktif; lead time ide → produksi | PMO |
| Technology | Platform maturity score (Modul 03) | Checklist |
| Data | Skor kualitas data; jumlah data product siap pakai | Data governance |
| Adoption & Scaling | Jumlah use case di PROD; % use case yang di-reuse lintas unit | Portal |

---

## 7. Stage Gate: POC → MVP → PROD → Scale

| Gate | Kriteria keluar (semua harus terpenuhi) |
|------|------------------------------------------|
| **Ide → POC** | Masalah bisnis jelas; value owner; risk tier ditetapkan; data tersedia |
| **POC → MVP** | Kualitas teknis ≥ threshold pada test set; potensi nilai terkonfirmasi; tidak ada blocker risiko |
| **MVP → PROD** | Pilot dengan user nyata: adopsi ≥ target, CSAT ≥ 4/5, kualitas stabil; impact assessment disetujui; guardrails, monitoring, dan runbook siap; rencana change management |
| **PROD → Scale** | Nilai terealisasi terbukti vs baseline; biaya per outcome sesuai business case; tidak ada insiden mayor 3 bulan; komponen dapat di-reuse |
| **Retire / Pivot** | Adopsi < 30% target setelah 3 bulan, atau ROI negatif setelah 2 kuartal, atau risiko tidak dapat dimitigasi |

**Kill criteria yang jelas sama pentingnya dengan kriteria lanjut.** Hentikan
inisiatif yang tidak memberi nilai dan alihkan sumber dayanya.

---

## 8. Ritme Review (Operating Cadence)

| Frekuensi | Forum | Fokus | Peserta |
|-----------|-------|-------|---------|
| Mingguan | Squad review | Kualitas, bug, feedback pengguna | Tim produk AI |
| Bulanan | AI Portfolio Review | Scorecard per use case, stage gate | PMO, value owner, IT |
| Kuartalan | AI Council | Nilai portofolio, risiko, re-alokasi anggaran | C-level, risk, HR |
| Semesteran | Strategic review | Readiness (Modul 02), Six Dimensions, update strategi (Modul 01) | Direksi |

---

## 9. AI Deployment Scorecard (ringkasan eksekutif)

| Pilar | Bobot | KPI utama | Target | Aktual | Status |
|-------|-------|-----------|--------|--------|--------|
| Value | 30% | ROI portofolio; nilai terealisasi (Rp) | | | 🟢🟡🔴 |
| Adoption & People | 25% | WAU/MAU; literasi AI; process adoption | | | |
| Performance & Quality | 20% | Task success rate; hallucination rate; biaya/outcome | | | |
| Risk & Governance | 15% | % use case ter-assess; insiden; kebocoran PII | | | |
| Capability | 10% | Indeks readiness; platform maturity | | | |
| **Skor total** | 100% | | | | |

**Aturan status:** 🟢 ≥ 90% target · 🟡 70–89% · 🔴 < 70%.
**Aturan override:** satu insiden risiko mayor membuat status pilar Risk 🔴,
apa pun skor lainnya.

---

## 10. Kesalahan Umum dalam Mengukur AI

1. Hanya mengukur **lisensi terpakai**, bukan perubahan proses dan nilai.
2. Tidak ada **baseline**, sehingga dampak tidak bisa dibuktikan.
3. Menghitung **jam dihemat** sebagai penghematan biaya tanpa realisasi.
4. Mengabaikan **biaya total** (token, integrasi, change management).
5. Mengukur kualitas hanya di awal; **drift** tidak dipantau.
6. KPI dimiliki oleh IT, bukan oleh **value owner bisnis**.
7. Tidak ada **kill criteria**, sehingga "pilot purgatory" berkepanjangan.
