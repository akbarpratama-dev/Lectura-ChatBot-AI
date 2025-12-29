# Dokumentasi Cloudflare WAF Rules

Project: Lectura ChatBot AI

Demi keamanan sistem, diterapkan 2 layer firewall pada Cloudflare WAF untuk melindungi endpoint n8n dari akses tidak sah.

## Rule 1: Allow Only Vercel Frontend

Mencegah akses langsung ke API/Webhook n8n kecuali request berasal dari WebApp resmi di Vercel.

- **Rule Name**: `Hanya Izinkan Web Lektura`
- **Action**: `Block`
- **Expression**:
  ```text
  (http.request.headers["referer"] does not contain "lectura-chat-bot-ai.vercel.app")
  ```

## Rule 2: Restrict HTTP Methods

Mencegah metode HTTP yang mencurigakan atau serangan bot, namun tetap mengizinkan fungsi Chat berjalan.

- **Rule Name**: `Block Weird Methods`
- **Action**: `Block`
- **Expression**:
  ```text
  (not http.request.method in {"GET" "POST" "OPTIONS"})
  ```
