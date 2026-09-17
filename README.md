# AI Image Classification & Application Deployment – DKB3263

## 1. Pengenalan Projek

Projek ini dibangunkan bagi memenuhi tugasan **DKB3263 – AI Image Classification & Application Deployment**. Projek menggunakan **Google Teachable Machine** sebagai platform utama untuk membina dan melatih model *image classification*, kemudian model tersebut diintegrasikan ke dalam aplikasi web menggunakan **TensorFlow.js**.

Aplikasi membolehkan pengguna memberikan input melalui **upload imej** atau **webcam**. Selepas imej diproses oleh model, aplikasi memaparkan kelas ramalan (*prediction/class*) dan **confidence score** untuk membantu pengguna memahami keputusan inferens model.

Projek ini dibangunkan sebagai *proof-of-concept* Computer Vision yang menunjukkan aliran lengkap daripada penyediaan dataset, latihan model, pengujian, eksperimen, integrasi aplikasi, deployment dan dokumentasi.

## 2. Objektif Projek

Objektif utama projek adalah untuk:

1. Membangunkan model *image classification* menggunakan Google Teachable Machine.
2. Menyediakan dataset yang sesuai dan mempunyai variasi imej untuk setiap kelas.
3. Menguji model menggunakan imej baharu yang tidak digunakan semasa latihan.
4. Menjalankan sekurang-kurangnya dua eksperimen model dan membandingkan keputusan.
5. Mengintegrasikan model yang telah dilatih ke dalam aplikasi web.
6. Memaparkan prediction, confidence score dan status keputusan kepada pengguna.
7. Menggunakan GitHub sebagai sistem pengurusan versi dan dokumentasi projek.

## 3. Teknologi yang Digunakan

| Teknologi | Kegunaan |
|---|---|
| Google Teachable Machine | Membina dan melatih model image classification |
| TensorFlow.js | Memuatkan dan menjalankan model dalam browser |
| HTML | Struktur aplikasi web |
| CSS | Reka bentuk dan antaramuka |
| JavaScript | Logik aplikasi dan proses inferens |
| FastAPI | Framework Python untuk membina backend/API jika diperlukan |
| Pydantic | Validasi dan pengurusan data request/response bagi backend FastAPI |
| Git | Version control |
| GitHub | Repository, dokumentasi dan deployment |
| GitHub Pages | Deployment aplikasi web |

## 4. Model Google Teachable Machine

Model yang digunakan dalam aplikasi ini ialah model **Google Teachable Machine** yang telah disediakan untuk projek.

**Model URL:**
https://teachablemachine.withgoogle.com/models/YOrkzhUi-/

Nama kelas, jumlah imej bagi setiap kelas dan keputusan training hendaklah direkodkan berdasarkan model sebenar yang digunakan. Maklumat tersebut tidak direka atau dianggarkan dalam repository ini.

## 5. Keperluan Projek

Projek ini mengambil kira keperluan utama tugasan DKB3263, termasuk:

- Minimum tiga kelas untuk image classification.
- Dataset yang mempunyai variasi dari segi sudut, jarak, pencahayaan dan latar belakang.
- Training model menggunakan Google Teachable Machine.
- Testing menggunakan data baharu yang tidak digunakan semasa training.
- Rekod prediction, confidence dan kesilapan klasifikasi.
- Sekurang-kurangnya dua eksperimen model.
- Aplikasi menerima input imej dan/atau webcam.
- Aplikasi memaparkan kelas ramalan dan confidence score.
- Status keputusan dan pengendalian confidence rendah.
- Fungsi reset/ulang ramalan.
- GitHub digunakan untuk version control dan dokumentasi.
- Sekurang-kurangnya dua penggunaan AI Code Assistant didokumentasikan.

## 6. Struktur Repository

```text
AI-Image-Classification-DKB3263/
│
├── index.html
├── README.md
├── .nojekyll
│
└── docs/
    ├── dataset.md
    ├── experiments.md
    ├── testing.md
    └── ai-code-assistant.md
```

### Penerangan fail

- **index.html** – aplikasi utama untuk upload imej, webcam, model inference, prediction dan confidence score.
- **README.md** – dokumentasi utama projek.
- **.nojekyll** – membantu deployment aplikasi statik melalui GitHub Pages.
- **docs/dataset.md** – dokumentasi sumber dan penyediaan dataset.
- **docs/experiments.md** – rekod dua eksperimen model dan perbandingan keputusan.
- **docs/testing.md** – rekod testing menggunakan imej baharu dan analisis kesilapan.
- **docs/ai-code-assistant.md** – rekod penggunaan AI Code Assistant.

## 7. Aliran Sistem

Aliran utama aplikasi adalah seperti berikut:

```text
User
  │
  ├── Upload Image
  │       atau
  └── Webcam
          │
          ▼
   Input Image / Frame
          │
          ▼
 Teachable Machine Model
      (TensorFlow.js)
          │
          ▼
 Prediction Probabilities
          │
          ▼
 Highest Confidence Class
          │
          ▼
 Prediction + Confidence + Status
          │
          ▼
        User
```

Model digunakan secara terus dalam browser menggunakan TensorFlow.js. Oleh itu, aplikasi semasa tidak memerlukan backend API untuk proses inferens asas. Kaedah ini membolehkan model dimuatkan dan dijalankan pada sisi pengguna (*client-side*).

## 8. Fungsi Aplikasi

Aplikasi menyediakan fungsi berikut:

### 8.1 Image Upload

Pengguna boleh memilih imej daripada komputer untuk diproses oleh model.

### 8.2 Webcam

Pengguna boleh menggunakan webcam untuk memberikan input secara langsung selepas memberikan kebenaran kamera kepada browser.

### 8.3 Prediction

Model menganalisis input dan menentukan kelas dengan kebarangkalian tertinggi.

### 8.4 Confidence Score

Aplikasi memaparkan confidence score bagi prediction yang dihasilkan oleh model.

### 8.5 Status Keputusan

Aplikasi memberikan indikator ringkas bagi membantu pengguna memahami keputusan, termasuk keadaan confidence yang rendah.

### 8.6 Reset

Pengguna boleh menetapkan semula input dan menjalankan prediction baharu.

## 9. FastAPI dan Pydantic

**FastAPI** ialah framework Python yang boleh digunakan untuk membina backend web dan API bagi aplikasi AI. Dalam projek image classification, FastAPI boleh bertindak sebagai pengantara antara aplikasi pengguna dengan model AI. Contohnya, aplikasi boleh menghantar fail imej kepada endpoint `POST /predict`, kemudian backend memproses imej menggunakan model dan mengembalikan keputusan prediction serta confidence dalam bentuk JSON.

Contoh aliran menggunakan FastAPI:

```text
User / Web App
      │
      ▼
   Image Input
      │
      ▼
POST /predict
      │
      ▼
 FastAPI Backend
      │
      ▼
 AI Classification Model
      │
      ▼
Prediction + Confidence
      │
      ▼
   JSON Response
      │
      ▼
     Web App
```

**Pydantic** pula digunakan bersama FastAPI untuk mentakrif dan mengesahkan struktur data yang dihantar atau diterima oleh API. Contohnya, keputusan inferens boleh distrukturkan sebagai:

```json
{
  "prediction": "Class Name",
  "confidence": 0.94
}
```

Walaupun FA DKB3263 menerangkan penggunaan **FastAPI + Pydantic jika backend Python diperlukan**, projek semasa menggunakan pendekatan **browser-based TensorFlow.js**. Model Teachable Machine dimuatkan terus dalam browser dan inferens dilakukan pada sisi pengguna. Oleh itu, FastAPI/Pydantic tidak diperlukan untuk aliran inferens semasa. Walau bagaimanapun, penerangan FastAPI dan Pydantic dimasukkan dalam dokumentasi untuk menunjukkan alternatif deployment backend Python yang ditetapkan dalam FA.

## 10. Training dan Eksperimen Model

Proses pembangunan model dilakukan menggunakan Google Teachable Machine:

1. Menentukan kelas/label yang diperlukan.
2. Mengumpul dan menyusun imej bagi setiap kelas.
3. Memastikan imej mempunyai variasi yang sesuai.
4. Memasukkan dataset ke dalam Google Teachable Machine.
5. Menjalankan training.
6. Menguji model.
7. Menjalankan eksperimen kedua dengan perubahan yang sesuai.
8. Membandingkan keputusan eksperimen.
9. Memilih model untuk digunakan dalam aplikasi.
10. Mengeksport/mengintegrasikan model ke dalam aplikasi.

Keputusan sebenar bagi kedua-dua eksperimen direkodkan dalam:

- [`docs/experiments.md`](docs/experiments.md)

## 11. Testing dan Evaluation

Model perlu diuji menggunakan imej baharu yang tidak digunakan semasa training. Setiap ujian direkodkan berdasarkan:

- Imej ujian
- Kelas sebenar
- Prediction model
- Confidence score
- Status betul/salah
- Catatan atau punca kemungkinan kesilapan

Rekod testing disediakan dalam:

- [`docs/testing.md`](docs/testing.md)

Nilai accuracy, confidence dan jumlah sampel hendaklah diisi berdasarkan keputusan ujian sebenar dan bukan nilai rekaan.

## 12. Dataset dan Data Preparation

Dokumentasi dataset disediakan dalam:

- [`docs/dataset.md`](docs/dataset.md)

Dataset perlu mempunyai sekurang-kurangnya tiga kelas dan sebaik-baiknya mempunyai variasi dari segi:

- Sudut objek
- Jarak objek
- Pencahayaan
- Latar belakang
- Kedudukan objek

Sumber dataset dan jumlah imej sebenar setiap kelas akan direkodkan selepas dataset akhir disahkan.

## 13. Deployment

Aplikasi ini direka sebagai aplikasi web statik dan boleh dideploy menggunakan **GitHub Pages**.

Untuk deployment:

1. Buka repository GitHub.
2. Pergi ke **Settings**.
3. Pilih **Pages**.
4. Pilih deployment daripada branch `main`.
5. Pilih folder `/ (root)`.
6. Simpan tetapan deployment.
7. Buka URL GitHub Pages yang diberikan oleh GitHub.

Selepas deployment berjaya, aplikasi boleh digunakan melalui browser tanpa perlu menjalankan server Python untuk inferens browser-based ini.

## 14. GitHub Version Control

GitHub digunakan untuk menyimpan kod, dokumentasi dan rekod perubahan projek. Repository menggunakan beberapa commit bermakna untuk menunjukkan proses pembangunan secara berperingkat.

Antara perubahan yang didokumentasikan termasuk:

- Penyediaan README projek.
- Pembangunan aplikasi web.
- Dokumentasi dataset.
- Dokumentasi eksperimen.
- Dokumentasi testing.
- Dokumentasi AI Code Assistant.
- Persediaan GitHub Pages.

**Repository:**
https://github.com/m-8974775-ui/AI-Image-Classification-DKB3263

## 15. AI Code Assistant

AI Code Assistant digunakan sebagai bantuan dalam proses pembangunan, seperti menjana fungsi, debugging, penambahbaikan kod dan dokumentasi.

Sekurang-kurangnya dua sesi penggunaan AI Code Assistant perlu direkodkan. Setiap sesi perlu menunjukkan:

- Tujuan penggunaan.
- Prompt yang digunakan.
- Hasil yang diberikan oleh AI.
- Perubahan yang dibuat pada projek.
- Proses semakan dan testing oleh pelajar.

Bukti penggunaan direkodkan dalam:

- [`docs/ai-code-assistant.md`](docs/ai-code-assistant.md)

AI-generated code tetap perlu disemak, difahami dan diuji oleh pelajar sebelum digunakan.

## 16. Etika, Keselamatan dan Integriti

Projek mematuhi prinsip asas berikut:

- Dataset hendaklah diperoleh daripada sumber yang sah atau dibenarkan.
- Maklumat peribadi tidak dimasukkan ke dalam repository.
- Password, API key dan access token tidak disimpan dalam GitHub.
- Penggunaan AI Code Assistant didokumentasikan.
- Kod yang dijana AI perlu disemak dan diuji.
- Laporan hendaklah menggambarkan sumbangan sebenar pelajar.

## 17. Dokumentasi Projek

Dokumen sokongan projek boleh dirujuk melalui folder `docs`:

| Dokumen | Kandungan |
|---|---|
| [Dataset](docs/dataset.md) | Sumber, kelas dan penyediaan dataset |
| [Experiments](docs/experiments.md) | Dua eksperimen dan perbandingan model |
| [Testing](docs/testing.md) | Testing, confidence dan error analysis |
| [AI Code Assistant](docs/ai-code-assistant.md) | Bukti penggunaan AI Code Assistant |

## 18. Status Projek

| Komponen | Status |
|---|---|
| Google Teachable Machine model | ✓ Integrated |
| Web application | ✓ Developed |
| Image upload | ✓ Available |
| Webcam input | ✓ Available |
| Prediction display | ✓ Available |
| Confidence display | ✓ Available |
| Reset function | ✓ Available |
| Low-confidence handling | ✓ Available |
| Dataset documentation | ✓ Prepared |
| Experiment documentation | ✓ Prepared |
| Testing documentation | ✓ Prepared |
| AI Code Assistant documentation | ✓ Prepared |
| GitHub repository | ✓ Available |
| GitHub Pages deployment | To be verified |
| Actual experiment results | To be recorded from real testing |
| Actual testing results | To be recorded from real testing |

## 19. Important Notes

Repository ini menyediakan struktur aplikasi dan dokumentasi projek. **Keputusan sebenar seperti nama kelas, jumlah imej, confidence, accuracy, keputusan eksperimen dan kesilapan model hendaklah dimasukkan berdasarkan model serta testing sebenar.**

Ini penting supaya laporan dan repository menggambarkan keputusan projek yang sebenar dan boleh dibuktikan semasa demo.

---

**Course:** DKB3263  
**Project:** AI Image Classification & Application Deployment  
**Platform:** Google Teachable Machine  
**Application:** HTML / CSS / JavaScript / TensorFlow.js  
**Optional Backend:** FastAPI / Pydantic  
**Version Control & Deployment:** GitHub / GitHub Pages
