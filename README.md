# 💡 **Tentang Aplikasi KOREKSI PRO v3.1**

# **Ringkasan Aplikasi**
Aplikasi ini adalah **sistem scoring/koreksi ujian otomatis** yang dirancang untuk mempermudah guru dalam mengoreksi lembar jawaban siswa. Aplikasi bekerja dengan basis **localStorage** (penyimpanan offline) dan mendukung berbagai tipe soal dengan bobot yang berbeda.

---

## **🎯 Fitur Utama**

### **1. Tipe-tipe Soal yang Didukung**
| Nomor | Tipe | Bobot Default | Keterangan |
|-------|------|---------------|-----------|
| 1-20 | **PG** (Pilihan Ganda) | 1 | Jawabannya hanya 1 huruf |
| 21-30 | **PGK** (Pilihan Ganda Kompleks) | 2 | Bisa jawab lebih dari 1 huruf |
| 31-35 | **JD** (Menjodohkan) | 3 | Pasangan jawaban |
| 36-40 | **BS** (Benar-Salah) | 3 | Kombinasi B/S |
| 41-45 | **ES** (Essay) | 6 | Koreksi manual oleh guru |

### **2. Komponen Utama**
- ✅ **Import Kunci Jawaban** - Template dengan bobot skor per soal
- ✅ **Import Data Jawaban Siswa** - Dari hasil scanning/Dola AI
- ✅ **Koreksi Interaktif** - Tabel soal-per-soal untuk review manual
- ✅ **Penyimpanan Database** - Offline dengan localStorage
- ✅ **Export Excel** - Laporan lengkap dengan nilai akhir
- ✅ **Analisis Butir Soal** - Statistik kesukaran soal per siswa
- ✅ **Backup & Restore** - Download/Upload database

---

## **📱 LANGKAH-LANGKAH PROSES PENGERJAAN**

### **FASE 1️⃣: PERSIAPAN & IMPORT KUNCI**

```
┌─────────────────────────────────────┐
│  DOWNLOAD FORMAT KUNCI JAWABAN      │
│  (Template_Kunci.xlsx)              │
└────────────┬────────────────────────┘
             │
             ↓
┌─────────────────────────────────────┐
│  UMPAN DATA KUNCI DI EXCEL:         │
│  • No Soal: 1, 2, 3... 45           │
│  • Kunci: A, B, C, D, atau BS       │
│  • Bobot: Skor per soal             │
└────────────┬────────────────────────┘
             │
             ↓
┌─────────────────────────────────────┐
│  IMPORT KUNCI (IMPORT KUNCI BUTTON) │
│  ✓ Sistem membaca & simpan di DB    │
└─────────────────────────────────────┘
```

**Contoh Data Kunci:**
```
No Soal | Kunci Jawaban | Bobot Skor
--------|---------------|----------
1       | A             | 1
21      | AB            | 2
31      | AC            | 3
36      | BBS           | 3
41      | (kosong)      | 6  ← Essay
45      | (kosong)      | 6  ← Essay
```

---

### **FASE 2️⃣: SCAN & AMBIL DATA JAWABAN SISWA**

```
┌──────────────────────────────────┐
│ MENGGUNAKAN APLIKASI DOLA/GEMINI │
│ (AI Chatbot)                     │
└────────────┬─────────────────────┘
             │
             ↓
┌──────────────────────────────────┐
│ LANGKAH 1: Ambil Foto Lembar     │
│ - Buka Dola/Gemini               │
│ - Klik icon kamera (+)           │
│ - Ambil foto lembar jawaban      │
└────────────┬─────────────────────┘
             │
             ↓
┌──────────────────────────────────┐
│ LANGKAH 2: Copy Prompt (Perintah)│
│ ────────────────────────────────  │
│ "Buatkan dalam format tabel Excel│
│ dengan kolom: Nama Siswa, S1     │
│ sampai S45. Gabungkan 9 karakter │
│ terakhir dari nomor peserta      │
│ dengan nama siswa dipisahkan      │
│ dengan tanda '-'. Data Jawaban   │
│ hanya huruf A, B, C, atau D      │
│ saja."                            │
└────────────┬─────────────────────┘
             │
             ↓
┌──────────────────────────────────┐
│ LANGKAH 3: Tunggu & Copy Hasil   │
│ - AI mengolah gambar (OCR)       │
│ - Hasilnya tabel Excel siap copy │
└────────────┬─────────────────────┘
             │
             ↓
┌──────────────────────────────────┐
│ LANGKAH 4: Paste ke Template     │
│ - Buka Template_Jawaban.xlsx     │
│ - Paste hasil Dola ke kolom A    │
│ - Simpan file                    │
└──────────────────────────────────┘
```

---

### **FASE 3️⃣: DOWNLOAD TEMPLATE JAWABAN**

```
┌──────────────────────────────────┐
│ DOWNLOAD FORMAT JAWABAN          │
│ (Template_Jawaban.xlsx)          │
└────────────┬─────────────────────┘
             │
             ↓
┌──────────────────────────────────┐
│ FILE TEMPLATE BERISI:            │
│ Header: Nama Siswa | S1 | S2 | ...│ S45
│ (Kosong - siap untuk diisi)      │
└──────────────────────────────────┘
```

---

### **FASE 4️⃣: IMPORT JAWABAN SISWA**

```
┌──────────────────────────────────┐
│ IMPORT JAWABAN (BUTTON UNGU)     │
│ Pilih file Template_Jawaban.xlsx │
│ yang sudah diisi data dari Dola  │
└────────────┬─────────────────────┘
             │
             ↓
┌──────────────────────────────────┐
│ SISTEM VALIDASI:                 │
│ ✓ Baca nama siswa                │
│ ✓ Mapping jawaban S1-S45         │
│ ✓ Masukkan ke ANTREAN            │
│ ✓ Tampilkan "Sisa: X SISWA"      │
└────────────┬─────────────────────┘
             │
             ↓
┌──────────────────────────────────┐
│ TABEL SIAP DIKOREKSI             │
│ Siswa pertama tampil otomatis    │
└──────────────────────────────────┘
```

---

### **FASE 5️⃣: KOREKSI INTERAKTIF**

```
┌─────────────────────────────────────────────┐
│          TAMPILAN TABEL KOREKSI             │
├─────────────────────────────────────────────┤
│ NO │ KUNCI │ JAWABAN SISWA │ BOBOT │ SKOR  │
├─────────────────────────────────────────────┤
│ 1  │   A   │      A        │   1   │   1   │ ✓ Benar
│ 2  │   B   │      C        │   1   │   0   │ ✗ Salah
│ 3  │   AB  │      A        │   2   │  1.0  │ Sebagian
│ 21 │   AB  │      AB       │   2   │   2   │ ✓ Benar
│... │ ...   │    ...        │ ...   │ ...   │
│ 41 │   B   │    (Kosong)   │   6   │   ?   │ ← ESSAY
│ 42 │   B   │    (Kosong)   │   6   │   ?   │ ← ESSAY
│ 45 │   B   │    (Kosong)   │   6   │   ?   │ ← ESSAY
└─────────────────────────────────────────────┘
```

#### **Logika Scoring Otomatis:**

| Tipe Soal | Cara Hitung | Contoh |
|-----------|------------|---------|
| **PG** | Jika jawaban = kunci → skor penuh | Kunci: A, Jawab: A → **1 skor** |
| **PGK/JD** | Cek jumlah cocok / total kunci × bobot | Kunci: AB, Jawab: A → **50% × 2 = 1** |
| **BS** | Hitung karakter cocok / total | Kunci: BBS, Jawab: BBS → **100% × 3 = 3** |
| **ES** | **MANUAL** - Guru input sendiri | Guru baca & tentukan skor |

---

### **FASE 6️⃣: KOREKSI MANUAL (ESSAY)**

```
📝 UNTUK SOAL ESSAY (S41-S45):
  
  ┌────────────────────────────────┐
  │ Guru membaca jawaban siswa     │
  │ di kolom "JAWABAN SISWA"       │
  └────────────┬───────────────────┘
               │
               ↓
  ┌────────────────────────────────┐
  │ Input SKOR di kolom "BOBOT"    │
  │ (Input bebas, default: 6)      │
  └────────────┬───────────────────┘
               │
               ↓
  ┌────────────────────────────────┐
  │ Tekan ENTER / Tab             │
  │ ✓ Sistem otomatis update skor │
  └────────────────────────────────┘
```

**Contoh Koreksi Essay:**
- **Kunci**: B
- **Jawaban Siswa**: "Fotosintesis adalah proses..."
- **Bobot**: 6 (maksimal)
- **Guru ubah ke**: 5 (karena jawaban sebagian benar)
- **Skor Akhir**: 5

---

### **FASE 7️⃣: SIMPAN & LANJUT KE SISWA BERIKUTNYA**

```
┌─────────────────────────────────────┐
│ SETELAH KOREKSI SELESAI:            │
│                                     │
│ [RESET] [LEWATI] [SIMPAN & LANJUT] │
└────────┬──────────┬─────────────────┘
         │          │
         │          └─→ Setelah verifikasi
         │              nama siswa
         └─→ Koreksi otomatis
             tanpa simpan
         
    ↓ KLIK "SIMPAN & LANJUT"
    
┌─────────────────────────────────────┐
│ ✓ DATA TERSIMPAN:                   │
│ • Nama siswa                        │
│ • Semua jawaban (S1-S45)            │
│ • Total skor murni                  │
│ • Nilai akhir (√murni × 10)        │
│                                     │
│ ✓ TAMPIL SISWA BERIKUTNYA           │
│   (Otomatis dari antrean)           │
└─────────────────────────────────────┘
```

---

### **FASE 8️⃣: DOWNLOAD HASIL EXCEL**

```
┌──────────────────────────────────────┐
│ TOMBOL: DOWNLOAD HASIL (EXCEL)       │
│ (Hijau, di bawah "Hasil Koreksi")    │
└────────────┬───────────────────────────┘
             │
             ↓
┌──────────────────────────────────────┐
│ FILE EXCEL BERISI:                   │
│ ─────────────────────────────────────│
│ REKAP NILAI SISWA                    │
│ Jenis Ujian  : PAS Ganjil           │
│ Mata Pelajaran: Matematika           │
│ Kelas        : XII IPA 1             │
│ Tanggal      : 2024-05-20            │
│ ─────────────────────────────────────│
│                                      │
│ | NO | NAMA | SKOR | NILAI | S1-45 | 
│ |----|------|-------|-------|-------|
│ | 1  | BUDI | 85.5  |  92.5 | A B C |
│ | 2  | SITI | 72.0  |  84.8 | A A B |
│ ... ... ...  ...    ...   ...      │
└──────────────────────────────────────┘
```

---

## **🔄 WORKFLOW LENGKAP (RINGKASAN)**

```
1. PERSIAPAN
   ↓
   Download Format Kunci → Isi Kunci & Bobot → Import Kunci
   ↓
2. SCAN DENGAN AI
   ↓
   Foto (Dola) → Copy Prompt → Tunggu AI → Copy Tabel
   ↓
3. PERSIAPAN TEMPLATE
   ↓
   Download Template Jawaban → Paste dari Dola → Simpan
   ↓
4. IMPORT & ANTREAN
   ↓
   Import Template → Siswa Masuk Antrean → Baca "Sisa: X"
   ↓
5. KOREKSI (PER SISWA)
   ↓
   Lihat Tabel → Input Essay Scores → Hitung Otomatis
   ↓
6. SIMPAN & LANJUT
   ↓
   Klik "SIMPAN & LANJUT" → Siswa Berikutnya Tampil
   ↓
7. SELESAI SEMUA SISWA
   ↓
   Download Excel → Analisis Butir Soal → Backup Data
   ↓
8. SELESAI ✅
```

---

## **💾 FITUR TAMBAHAN**

### **A. Analisis Butir Soal**
- Menampilkan persentase siswa yang menjawab benar per soal
- **Mudah** (>70%) 🟢 | **Sedang** (30-70%) 🟠 | **Sulit** (<30%) 🔴
- **Export ke PDF** untuk laporan analisis

### **B. Backup & Restore Database**
- **EXPORT DB**: Download semua data sebagai `.json`
- **RESTORE**: Upload file backup untuk recover data
- **HAPUS DB**: Bersihkan semua data (⚠️ permanent)

### **C. Edit Hasil Koreksi**
- Klik nama siswa di list → Tabel sudah terisi
- Ubah jawaban/skor → Klik "SIMPAN & LANJUT" untuk update

---

## **⚡ TIPS PENTING**

✅ **Pastikan:**
- Kunci jawaban sudah di-import sebelum import jawaban siswa
- Format Excel Template sudah sesuai (Nama di kolom A, S1-S45 di kolom B dst)
- Essay scores diisi manual oleh guru (tidak otomatis)
- Mata Pelajaran **WAJIB** diisi sebelum download Excel

❌ **Hindari:**
- Menghapus database tanpa backup
- Browser direfresh saat koreksi sedang berlangsung (data hilang)
- File Excel dengan format yang tidak sesuai.

## **SEMOGA BEEMANFAAT...**