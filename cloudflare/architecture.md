# Arsitektur Sistem Baru (Cloudflare Integration)

Sistem ini telah dimigrasikan dari arsitektur berbasis Ngrok (temporary) ke Cloudflare Zero Trust Tunnel (permanent) untuk meningkatkan stabilitas, keamanan, dan performa.

## Diagram Topologi

[ User / WebApp Vercel ]
⬇ (HTTPS Request)
⬇
[ Cloudflare Edge Network ] 🛡️
├── DDoS Protection
├── SSL/TLS Encryption (Full)
└── WAF (Web Application Firewall)
├── Filter: Cek Referer (Must be Vercel)
└── Filter: Cek Method (GET/POST/OPTIONS)
⬇
⬇ (Encrypted Tunnel)
⬇
[ Laptop Lokal: Akbar-MacBook-Air-M1 ] 💻
├── Cloudflared Service (Daemon)
│ └── Meneruskan request ke localhost:5678
│
└── [ Docker Container: n8n ] 🐳
├── Workflow: Chat AI (RAG)
├── Workflow: Upload PDF
└── Database: PostgreSQL/Internal

## Keunggulan Arsitektur Baru

1. **Keamanan Bertingkat**:
   - IP Address laptop tidak terekspos ke publik (disembunyikan oleh Cloudflare).
   - Firewall memblokir akses ilegal sebelum menyentuh server lokal.
2. **Stabilitas**:
   - Tidak ada batasan sesi waktu (seperti Ngrok Free yang expired tiap 2 jam).
   - Tunnel berjalan otomatis sebagai _System Service_ saat laptop menyala.
3. **Enkripsi**:
   - Komunikasi End-to-End terenkripsi menggunakan sertifikat SSL Cloudflare.

## Routing Domain

- **WebApp**: `https://lectura-chat-bot-ai.vercel.app` (Frontend)
- **Backend**: `https://n8n.lectura.my.id` (n8n Dashboard & Webhook Endpoint)
