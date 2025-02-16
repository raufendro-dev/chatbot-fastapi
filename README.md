# 🚀 FastAPI Chatbot dengan OpenAI Assistant & Pengambilan Data MySQL

Proyek ini adalah chatbot berbasis FastAPI yang terintegrasi dengan OpenAI's Assistant API, dikombinasikan dengan pengambilan data MySQL dan unggahan otomatis ke OpenAI's vector store. Bot ini mempertahankan sesi pengguna dan mendukung sinkronisasi data otomatis.

---

## 📌 Fitur

✅ **Backend FastAPI** - Server API yang ringan dan efisien.

✅ **Integrasi OpenAI Assistant** - Menangani percakapan pengguna.

✅ **Manajemen Sesi** - Melacak interaksi pengguna.

✅ **Pengambilan Data dari MySQL** - Mengambil dan membersihkan data.

✅ **Unggahan File Otomatis ke OpenAI** - Memastikan sinkronisasi data.

✅ **Dukungan Multithreading** - Menjalankan tugas latar belakang untuk pembaruan data.

---

## 🛠️ Instalasi & Pengaturan

### 1️⃣ Clone Repository
```sh
 git clone https://github.com/raufendro-dev/chatbot-fastapi.git
 cd chatbot-fastapi
```

### 2️⃣ Install Dependensi
```sh
pip install -r requirements.txt
```

### 3️⃣ Atur Variabel Lingkungan
Buat file `.env` dan tambahkan berikut ini:
```env
API_KEY=your_openai_api_key
ASSISTANT_ID=your_openai_assistant_id
VECTOR_STORE_ID=your_openai_vector_store_id
```

### 4️⃣ Jalankan Server FastAPI
```sh
uvicorn api:app --host 0.0.0.0 --port 7878 --workers 4
```
*️⃣ Sesuaikan jumlah worker dengan jumlah core CPU yang dimiliki.

---

## 📡 Endpoint API

### ➤ Chat dengan Asisten
**POST** `/chat`

🗒️ chat_id can be phone number or session chat based on your system
```json
{
    "chat_id": "user123",
    "message": "Halo, bot!"
}
```
💬 **Respon:**
```json
{
    "response":"Halo, Apa kabar."
}
```

### ➤ Reset Semua Sesi
**POST** `/reset`
```json
{
    "message": "Semua sesi telah direset!"
}
```

---

## 📂 Sinkronisasi Data MySQL

✅ Mengambil data dari MySQL.
✅ Membersihkan data (menghapus tag HTML).
✅ Menyimpan dalam file JSON (`data/what_ever_you_want.json`).
✅ Mengunggah ke OpenAI.

### ➤ Alur Pemrosesan Data
1️⃣ **Mengambil Data dari MySQL** → `fetch_data()`
2️⃣ **Menghapus Tag HTML** → `remove_html_tags()`
3️⃣ **Memeriksa Pembaruan** → `get_data()`
4️⃣ **Mengunggah ke OpenAI** → `upload_to_openai()`
5️⃣ **Mengelola File Vektor** → `create_vector()` & `delete_vector()`

---

## 🔄 Tugas Latar Belakang Otomatis
Script ini menjalankan **thread latar belakang** yang memeriksa data MySQL baru setiap **10 detik** dan memperbarui OpenAI vector store jika diperlukan.

```python
threading.Thread(target=run_function, args=(get_data,)).start()
```

---

## 🎯 Pengembangan di Masa Depan
- ✅ Dukungan WebSocket untuk Chat Real-Time
- ✅ Autentikasi untuk Keamanan API
- ✅ Dashboard untuk Memantau Chat & Data

💡 Jangan ragu untuk berkontribusi & meningkatkan proyek ini!

---

## 💰 Bukan Open Source
Jika ingin menggunakan, hubungi raufendro@gmail.com atau kirim pesan ke LinkedIn Rauf Endro Widagdo

