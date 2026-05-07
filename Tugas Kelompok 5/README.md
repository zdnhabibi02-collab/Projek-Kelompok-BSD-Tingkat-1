# Projek Kelompok BSD Tingkat 1

Sistem monitoring sensor tanaman tomat secara real-time menggunakan MQTT dan MongoDB.

## 📋 Deskripsi

Project ini terdiri dari:
- **Publisher (pub_sensor.py)**: Generate data sensor secara random
- **Subscriber (sub_sensor.py)**: Subscribe MQTT dan simpan data ke MongoDB, serta deteksi alert
- **Dashboard (app.py)**: Flask web dashboard untuk visualisasi data
- **Koneksi (koneksi.py)**: Fungsi helper untuk koneksi MQTT dan MongoDB

## 🚀 Setup

### 1. Clone Repository
```bash
git clone https://github.com/zdnhabibi02-collab/Projek-Kelompok-BSD-Tingkat-1.git
cd "Projek-Kelompok-BSD-Tingkat-1"
```

### 2. Buat File `.env`
Buat file `.env` di root project dengan konfigurasi:
```
MQTT_BROKER=170.106.137.233
MQTT_PORT=34423
MQTT_USER=c1
MQTT_PASS=apaan
```

### 3. Install Dependencies
```bash
pip install paho-mqtt pymongo flask python-dotenv
```

## 🏃 Cara Menjalankan

Buka 3 terminal terpisah untuk menjalankan:

### Terminal 1: Publisher (Generate Data)
```bash
python pub_sensor.py
```

### Terminal 2: Subscriber (Process Data & Alert)
```bash
python sub_sensor.py
```

### Terminal 3: Dashboard (Flask)
```bash
python app.py
```

Akses dashboard di: `http://localhost:5000`

## 📁 Struktur File

```
.
├── pub_sensor.py          # Generate sensor data
├── sub_sensor.py          # Subscribe MQTT & simpan ke DB
├── app.py                 # Flask dashboard
├── koneksi.py             # Helper functions untuk koneksi
├── analisis_dashboard.py  # Analytics module
├── templates/
│   └── index.html        # Dashboard HTML
├── .env                   # Konfigurasi (jangan commit)
├── .gitignore             # Files yang diabaikan Git
└── README.md              # File ini
```

## 📊 Parameter Alert

Subscriber akan mendeteksi alert berdasarkan parameter berikut:

| Parameter | Kondisi Alert |
|-----------|---------------|
| Kelembapan Tanah | < 40% (kering) atau > 80% (basah) |
| PM2.5 | > 150 (berbahaya) |
| Cahaya | < 500 fc (redup) atau > 8000 fc (terik) |
| Suhu | < 15°C (dingin) atau > 32°C (panas) |

## 🔒 Keamanan

- Kredensial (username, password) disimpan di file `.env` (jangan di-commit)
- File `.env` sudah di-ignore oleh `.gitignore`
- Koneksi MQTT dan MongoDB menggunakan environment variables dari `koneksi.py`

## 📦 Dependencies

- `paho-mqtt` - MQTT client
- `pymongo` - MongoDB driver
- `flask` - Web framework
- `python-dotenv` - Load environment variables

## 📝 Catatan

- Pastikan MQTT Broker dan MongoDB sudah running sebelum menjalankan script
- Data sensor disimpan di database `kelompok5_ZAIDAN_HABIBI`
- Koleksi `sensor_tomat` untuk menyimpan data sensor
- Koleksi `alert` untuk menyimpan log alert
