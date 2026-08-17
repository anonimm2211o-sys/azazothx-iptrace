# AZAZOTHX-IPTRACE 🔎

AZAZOTHX-IPTRACE adalah web-based network intelligence dan infrastructure analysis tool untuk mempelajari hubungan antara domain, DNS, passive intelligence, HTTP infrastructure, dan network connectivity.

«EDUCATIONAL / SECURITY RESEARCH PROJECT

Hasil IPTRACE berupa data observasi dan kandidat infrastruktur. IP yang ditemukan tidak otomatis berarti origin server sebenarnya.»

⚡ Features

- 🌐 Domain lookup
- 🔎 Passive DNS discovery
- 📜 Certificate Transparency lookup
- ☁️ Cloudflare detection
- 📡 Infrastructure candidate discovery
- 🔌 TCP connectivity / port check
- 📊 Source aggregation
- 🖥️ Real-time styled terminal interface
- 🚀 Vercel Serverless API

🧠 How It Works

                     ┌─────────────────┐
                     │     DOMAIN      │
                     └────────┬────────┘
                              │
                              ▼
                  ┌──────────────────────┐
                  │   IPTRACE ENGINE     │
                  └──────────┬───────────┘
                             │
             ┌───────────────┼───────────────┐
             ▼               ▼               ▼
        Certificate      Passive DNS       DNS Data
        Transparency     / History
             │               │               │
             └───────────────┼───────────────┘
                             ▼
                    ┌─────────────────┐
                    │ IP Correlation  │
                    │ + Deduplication │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Candidate IPs   │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Network Check   │
                    └────────┬────────┘
                             │
                             ▼
                         RESULT 🔎

IPTRACE tidak perlu mengakses server secara langsung untuk melakukan passive discovery. Sistem menggabungkan informasi yang tersedia dari sumber publik, kemudian menyajikannya sebagai hasil analisis.

📡 Current API Flow

Frontend mengirim request:

GET /api/lookup?domain=example.com

Backend kemudian melakukan beberapa tahap:

DOMAIN
  ↓
Cloudflare / HTTP detection
  ↓
Certificate Transparency
  ↓
Passive DNS source
  ↓
IP aggregation
  ↓
Candidate classification
  ↓
TCP connectivity check
  ↓
JSON response

📦 Example Response

{
  "domain": "example.com",
  "cloudflare_detected": false,
  "origin_ip": "203.0.113.10",
  "discovered_ips": [
    "203.0.113.10"
  ],
  "open_ports": [
    80,
    443
  ],
  "sources": {
    "crt_sh": [],
    "hackertarget": [
      "203.0.113.10"
    ]
  }
}

«"origin_ip" pada implementasi saat ini merupakan IP kandidat pertama yang ditemukan oleh engine. Field tersebut tidak boleh dianggap sebagai bukti origin server tanpa validasi tambahan.»

🖥️ Frontend

Frontend menggunakan interface terminal-style dengan:

- AZAZOTHX-IPTRACE branding
- Live clock WIB
- Domain input
- Quick domain buttons
- Lookup status log
- IP result card
- Domain information
- Network port information
- Source information
- Background video support

Frontend menggunakan API backend:

const API_BASE =
  'https://backend-iptrace.vercel.app/api/lookup';

🛠️ Tech Stack

Frontend
├── HTML
├── CSS
└── Vanilla JavaScript

Backend
├── Node.js
├── Serverless Functions
└── Vercel

Intelligence Sources
├── Certificate Transparency
├── Passive DNS
├── DNS
└── HTTP metadata

🚀 Deployment

Project ini dapat digunakan dengan Vercel.

Frontend:

index.html
background.mp4

Backend:

api/
└── lookup.js

Setelah project terhubung ke Vercel:

vercel --prod

Pastikan "API_BASE" pada frontend mengarah ke deployment backend yang benar.

🔐 Security & Responsible Use

IPTRACE dibuat untuk:

- pembelajaran network security
- security research
- pengujian domain/infrastruktur milik sendiri
- demonstrasi passive intelligence
- analisis konfigurasi jaringan

Gunakan tool hanya pada sistem yang Anda miliki atau memiliki izin untuk menguji.

Jangan menganggap hasil passive discovery sebagai bukti kepemilikan atau origin server.

⚠️ Limitations

IP yang ditemukan dapat berupa:

CDN
Proxy
Hosting infrastructure
Shared infrastructure
Historical IP
Load balancer
Edge server
Candidate origin

Karena itu:

IP FOUND ≠ ORIGIN VERIFIED

Perubahan DNS, CDN, hosting provider, dan konfigurasi jaringan juga dapat menyebabkan hasil berbeda pada waktu yang berbeda.

📊 Project Status

Frontend              ████████████████████ 100%
Backend API           ████████████████████ 100%
DNS Lookup            ████████████████████ 100%
Passive Discovery     ██████████████████░░  90%
Cloudflare Detection  ████████████████████ 100%
Port Connectivity     ████████████████████ 100%
Origin Verification   ████████░░░░░░░░░░░░  40%

Project masih dalam tahap pengembangan dan eksperimen.

---

AZAZOTHX-IPTRACE

NETWORK INTELLIGENCE
INFRASTRUCTURE ANALYSIS
SECURITY RESEARCH

Observe.
Analyze.
Understand.

AZAZOTHX // IPTRACE
