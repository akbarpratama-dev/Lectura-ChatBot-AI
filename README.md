# Lektura - RAG Chatbot untuk Skripsi

Deskripsi
- Lektura adalah antarmuka frontend ringan untuk chatbot RAG (Retrieval-Augmented Generation) yang membantu membaca dokumen (skripsi, jurnal, paper) dan menjawab pertanyaan berbasis dokumen yang diunggah. Frontend berkomunikasi dengan webhook n8n untuk pengiriman chat dan upload dokumen.

Tech stack
- HTML (struktur): [index.html](index.html)  
- CSS (styling): [style.css](style.css)  
- JavaScript (interaksi & state lokal): Vanilla JS (localStorage, Fetch API) — lihat fungsi seperti [`handleSend`](index.html), [`generateUUID`](index.html), [`initTextLoop`](index.html), [`initWelcomeTitleAnimation`](index.html), dan [`saveFileHistory`](index.html).  
- Ikon & font: Font Awesome, Google Fonts  
- Backend integrasi: webhook n8n (konfigurasi URL di [index.html](index.html))  
- Asset statis: [assets/](assets/)

Cara menjalankan
1. Buka file [index.html](index.html) di browser (file statis, tidak perlu build).
2. Untuk berfungsi penuh, ganti variabel webhook di [index.html](index.html) dengan endpoint n8n Anda.

Referensi file utama
- [index.html](index.html) — UI, logika JS, webhook URL
- [style.css](style.css) — stylesheet utama (jika ingin pisahkan CSS dari HTML inline)
- [assets/](assets/) — gambar dan ikon proyek

Catatan singkat
- Chat & riwayat disimpan di localStorage.
- Upload file dikirim ke N8N_UPLOAD_URL yang didefinisikan di [index.html](index.html).
