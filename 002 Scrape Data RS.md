# JUDUL: Cara Scrape Data Rumah Sakit dari Google Maps dalam 5 Menit (Python + Selenium)

**Durasi:** 200 detik  
**Gaya:** Storytelling teknis dengan bahasa santai, mudah dipahami pemula

---

## 📋 BREAKDOWN DETIK-DEMI-DETIK

### **HOOK (0–15 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 0–5 | Lo pernah kepikiran nggak... gimana cara ambil data rumah sakit dari Google Maps—otomatis, tanpa manual copy-paste? | Tunjuk Google Maps di browser |
| 6–10 | Bayangin lo harus kumpulin 100 rumah sakit di Sumatera Utara... manual? Capek banget, bro! | Gesture "capek banget" |
| 11–15 | Nah, hari ini gue bakal kasih tau cara otomatisin itu pake Python + Selenium dalam 5 menit aja! | Senyum, jari tunjuk layar |

---

### **CHAPTER 1: Apa Itu Web Scraping dengan Selenium? (15–50 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 15–22 | Selenium itu kayak robot yang bisa kontrol browser lo. Lo kasih perintah, dia yang klik, scroll, ambil data—otomatis! | Gesture "robot" |
| 23–30 | Bedanya sama library scraping biasa? Selenium bisa handle website yang pake JavaScript berat—kayak Google Maps yang dinamis banget. | Tunjuk loading Google Maps |
| 31–38 | Jadi kalau website-nya butuh klik tombol, scroll halaman, atau tunggu animasi—Selenium jagoannya! | Gesture "scroll" |
| 39–45 | Tools yang kita pake: Python + Selenium + ChromeDriver. Semua gratis, open-source, dan powerful banget. | Tunjuk logo Python & Chrome |
| 46–50 | *(jeda napas)* | Ambil napas, minum air |

---

### **CHAPTER 2: Setup Awal — Install Library (50–90 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 50–58 | Pertama, lo harus punya Python udah terinstall. Belum? Download di python.org—gratis. Cek pake `python --version` di terminal. | Tunjuk website python.org |
| 59–66 | Lalu buka terminal atau CMD, install 3 library penting ini satu per satu: | Hitung pakai jari |
| 67–72 | Pertama: `pip install selenium` —ini library utamanya buat otomatisasi browser. | Ketik di terminal |
| 73–78 | Kedua: `pip install webdriver-manager` —biar ChromeDriver otomatis update, nggak perlu download manual. | Ketik lagi |
| 79–83 | Ketiga: `pip install csv` —untuk export data ke file CSV (biasanya udah ada di Python). | Ketik lagi |
| 84–90 | Kalau udah semua, buat file baru namanya `scrape_hospital.py`. Bisa pake VS Code, PyCharm, atau Notepad++—bebas. | Buka code editor, buat file baru |

---

### **CHAPTER 3: Breakdown Kode — Baris demi Baris (90–170 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 90–97 | Oke, sekarang kita bahas kode-nya. Baris pertama: `from selenium import webdriver` —ini buat import library Selenium yang tadi udah kita install. | Highlight baris 1 di code |
| 98–105 | Baris kedua & ketiga: import Service dan By —ini buat setup driver dan cara cari elemen di website. | Highlight baris 2-3 |
| 106–113 | Baris keempat: `from webdriver_manager.chrome import ChromeDriverManager` —ini yang bikin ChromeDriver otomatis install & update. Gila praktis! | Highlight baris 4 |
| 114–120 | Baris kelima & enam: import time dan csv —time buat kasih jeda, csv buat export data nanti. | Highlight baris 5-6 |
| 121–130 | Nah, bagian setup WebDriver. Ada 2 mode: **headless** (browser jalan di background, nggak kelihatan) atau **normal** (browser terbuka, lo bisa liat prosesnya). | Gesture "lihat proses" |
| 131–138 | Di kode ini, gue comment dulu mode headless-nya biar lo bisa liat proses scraping berjalan. Kalau udah jago, uncomment buat bikin lebih cepat. | Tunjuk comment di code |
| 139–146 | Baris `driver = webdriver.Chrome(...)` —ini yang bikin Chrome terbuka otomatis. ChromeDriverManager otomatis download driver yang sesuai versi Chrome lo. | Highlight baris setup driver |
| 147–154 | `url = 'https://www.google.com/search?q=rs+di+Sumatera+Utara...'` —ini target pencarian Google Maps. Lo bisa ganti keyword-nya sesuai kebutuhan. | Highlight URL |
| 155–162 | `driver.get(url)` —perintah buat buka URL tersebut di browser. `time.sleep(3)` —tunggu 3 detik biar halaman selesai loading. | Highlight baris get & sleep |
| 163–170 | `all_results = []` —list kosong buat nyimpen semua data rumah sakit yang kita ambil. | Highlight list kosong |

---

### **CHAPTER 4: Logika Scraping — Ambil Data dari Setiap Halaman (170–230 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 170–178 | Sekarang masuk ke bagian inti: loop `while True`. Ini artinya program bakal jalan terus sampe ketemu break. | Highlight while loop |
| 179–186 | `results = driver.find_elements(By.CLASS_NAME, 'VkpGBb')` —ini nyari semua elemen rumah sakit di halaman. Class 'VkpGBb' itu class khusus Google buat hasil pencarian. | Highlight find_elements |
| 187–194 | `if not results: break` —kalau nggak nemu hasil, program berhenti. Ini safety check biar nggak error. | Highlight if not results |
| 195–202 | Terus ada loop `for result in results` —ini buat ambil data dari setiap rumah sakit satu per satu. | Highlight for loop |
| 203–210 | `name = result.find_element(By.CLASS_NAME, 'dbg0pd').text` —ambil nama rumah sakit dari class 'dbg0pd'. | Highlight nama |
| 211–218 | `address = result.find_element(By.CLASS_NAME, 'rllt__details')...` —ambil alamat dari class 'rllt__details', terus ambil div kedua. | Highlight alamat |
| 219–226 | `rating = result.find_element(By.CLASS_NAME, 'OSrXXb').text` —ambil rating dari class 'OSrXXb'. | Highlight rating |
| 227–230 | `link = result.find_element(By.CLASS_NAME, 'yYlJEf').get_attribute('href')` —ambil link website dari class 'yYlJEf'. | Highlight link |

---

### **CHAPTER 5: Navigate ke Halaman Berikutnya (230–260 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 230–237 | Setelah ambil semua data di halaman ini, program coba cari tombol "Next" buat lanjut ke halaman berikutnya. | Gesture "next page" |
| 238–245 | `next_button = driver.find_element(By.ID, 'pnnext')` —cari tombol Next pake ID 'pnnext'. Ini ID khusus Google buat tombol next. | Highlight next_button |
| 246–253 | `next_button.click()` —klik tombol Next! Terus `time.sleep(3)` lagi buat tunggu halaman baru loading. | Highlight click() |
| 254–260 | Kalau tombol Next nggak ketemu (artinya udah di halaman terakhir), program print "No more pages" terus break dari loop. | Highlight except block |

---

### **CHAPTER 6: Export ke CSV — Simpan Datanya! (260–290 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 260–267 | Setelah semua data terkumpul, sekarang waktunya export! Kita pake library CSV bawaan Python. | Gesture "export" |
| 268–275 | `with open('hospital_data_selenium.csv', 'w', encoding='utf-8') as file` —buka file CSV baru, mode write, encoding UTF-8 biar karakter Indonesia nggak error. | Highlight open() |
| 276–283 | `writer = csv.DictWriter(file, fieldnames=['name', 'address', 'rating', 'link'])` —setup writer dengan 4 kolom: nama, alamat, rating, link. | Highlight DictWriter |
| 284–288 | `writer.writeheader()` —tulis header kolom di baris pertama. | Highlight writeheader() |
| 289–290 | `for result in all_results: writer.writerow(result)` —loop semua data, tulis ke CSV satu per satu. | Highlight writerow() |

---

### **CHAPTER 7: Jalankan & Lihat Hasilnya! (290–320 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 290–298 | Oke, kode udah siap. Sekarang tinggal jalanin! Buka terminal, ketik: `python scrape_hospital.py` —enter! | Ketik di terminal |
| 299–306 | Browser Chrome bakal terbuka otomatis, terus pergi ke Google Maps, mulai scrape data rumah sakit satu per satu. | Tunjuk browser yang jalan |
| 307–314 | Lo bisa liat prosesnya: scroll otomatis, klik tombol Next, ambil data... semua jalan sendiri kayak robot! | Gesture "otomatis" |
| 315–320 | Setelah selesai, browser otomatis tutup, dan muncul file baru namanya `hospital_data_selenium.csv`. | Tunjuk file CSV |

---

### **CHAPTER 8: Lihat Data di Excel/Google Sheets (320–350 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 320–327 | Buka file CSV-nya pake Excel atau Google Sheets. Lo bakal liat semua data rapih dalam tabel: nama, alamat, rating, link website. | Buka Excel/Sheets |
| 328–335 | Tinggal sortir, filter, atau export ke format lain. Mau jadi database? Tinggal import ke MySQL atau MongoDB. | Gesture "database" |
| 336–343 | Bayangin kalau lo harus manual copy-paste 100 rumah sakit... bisa berjam-jam! Dengan script ini? 2 menit selesai. | Gesture "cepet banget" |
| 344–350 | *(jeda napas)* | Tatap kamera, ekspresi "keren kan?" |

---

### **CHAPTER 9: Use Cases — Buat Apa Sih Ini? (350–390 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 350–357 | "Terus... buat apa sih scrape data rumah sakit?" Pertanyaan bagus! Ini beberapa use case-nya: | Hitung pakai jari |
| 358–365 | **Pertama: Riset pasar kesehatan.** Buat startup kesehatan? Lo butuh data kompetitor—rumah sakit mana aja yang ada di daerah lo. | Gesture "riset" |
| 366–373 | **Kedua: Database publik.** Buat website direktori rumah sakit? Lo bisa update data otomatis tiap minggu pake script ini. | Gesture "website" |
| 374–381 | **Ketiga: Analisis lokasi.** Mau buka klinik baru? Cek dulu rumah sakit kompetitor di sekitar lokasi target. | Gesture "analisis" |
| 382–387 | **Keempat: Emergency app.** Buat aplikasi darurat yang butuh data rumah sakit terdekat—update otomatis! | Gesture "app" |
| 388–390 | *(jeda napas)* | Angguk pelan |

---

### **CHAPTER 10: Warning & Etika (390–420 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 390–398 | TAPI—ada beberapa hal yang harus lo inget. Pertama: jangan scrape terlalu cepat atau terlalu banyak. Google bisa block IP lo. | Gesture "stop" |
| 399–406 | Kedua: tambah `time.sleep()` yang cukup antar halaman—minimal 3 detik biar nggak kayak bot spam. | Highlight time.sleep |
| 407–414 | Ketiga: jangan gunain buat hal ilegal—spam, phising, atau jual data tanpa izin. Etika, bro! | Ekspresi serius |
| 415–420 | Keempat: cek Terms of Service Google. Scraping untuk riset pribadi biasanya okay, tapi untuk komersial bisa kena masalah. | Geleng kepala |

---

### **CLOSING & CALL TO ACTION (420–440 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 420–427 | Jadi... sekarang lo udah tau cara scrape data rumah sakit dari Google Maps otomatis pake Python + Selenium. Gampang kan? | Senyum |
| 428–433 | Coba praktekin sendiri—ambil data restoran, hotel, atau toko di daerah lo. Tinggal ganti keyword di URL-nya aja! | Gesture "coba sekarang" |
| 434–438 | Kalau berhasil, komen di bawah! Share juga data apa yang lo scrape—siapa tau bisa jadi referensi buat yang lain. | Tunjuk kolom komentar |
| 439–440 | Sampai jumpa di video berikutnya! | Wave tangan |

---

## 📝 FULL CODE YANG SUDAH DIJELASKAN

```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By
from webdriver_manager.chrome import ChromeDriverManager

import time
import csv

# Setup WebDriver
# options = webdriver.ChromeOptions()
# options.add_argument("--headless")  # Operasikan di background tanpa membuka browser
# driver = webdriver.Chrome(options=options)

# Set up Selenium WebDriver
options = webdriver.ChromeOptions()
# Uncomment next line for headless mode
# options.add_argument("--headless")  
driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()), options=options)

# URL yang akan diambil datanya
url = 'https://www.google.com/search?q=rs+di+Sumatera+Utara&sca_esv=3539a24babae7179&biw=1745&bih=828&tbm=lcl&ei=xgNYZ6PcJ72V4-EPgqny8Aw&ved=0ahUKEwij1_f865yKAxW9yjgGHYKUHM4Q4dUDCAk&uact=5&oq=rs+di+Sumatera+Utara&gs_lp=Eg1nd3Mtd2l6LWxvY2FsIhRycyBkaSBTdW1hdGVyYSBVdGFyYTIFEAAYgAQyBhAAGBYYHjIGEAAYFhgeMgYQABgWGB4yBhAAGBYYHjIGEAAYFhgeMgYQABgWGB4yBhAAGBYYHjIGEAAYFhgeMgYQABgWGB5I1iBQ5AVYqRxwAHgAkAEBmAGxAaABvQ-qAQQ2LjEzuAEDyAEA-AEB-AECmAIGoAKLBcICCBAAGIAEGKIEwgIFECEYoAHCAggQABgWGAoYHpgDAIgGAZIHAzMuM6AH0UA&sclient=gws-wiz-local#rlfi=hd:;si:;mv:[[3.7209831999999996,98.890147],[3.4804415,98.474175]];tbs:lrf:!1m4!1u3!2m2!3m1!1e1!1m4!1u2!2m2!2m1!1e1!2m1!1e2!2m1!1e3!3sIAE,lf:1,lf_ui:2'

# Buka URL
driver.get(url)
time.sleep(3)  # Tunggu beberapa detik supaya halaman sepenuhnya dimuat

# Inisialisasi untuk menyimpan data yang diambil
all_results = []

# Loop untuk mengambil data dari beberapa halaman
while True:
    # Ambil elemen hasil pencarian rumah sakit
    results = driver.find_elements(By.CLASS_NAME, 'VkpGBb')
    if not results:
        print("No results found.")
        break
    
    # Loop untuk mengambil setiap hasil dari halaman
    for result in results:
        # Mengambil nama rumah sakit
        name = result.find_element(By.CLASS_NAME, 'dbg0pd').text if result.find_element(By.CLASS_NAME, 'dbg0pd') else 'No Name'
        
        # Mengambil alamat rumah sakit
        address = result.find_element(By.CLASS_NAME, 'rllt__details').find_elements(By.TAG_NAME, 'div')[1].text if result.find_element(By.CLASS_NAME, 'rllt__details') else 'No Address'
        
        # Mengambil rating rumah sakit
        rating = result.find_element(By.CLASS_NAME, 'OSrXXb').text if result.find_element(By.CLASS_NAME, 'OSrXXb') else 'No Rating'
        
        # Mengambil link website rumah sakit
        link = result.find_element(By.CLASS_NAME, 'yYlJEf').get_attribute('href') if result.find_element(By.CLASS_NAME, 'yYlJEf') else 'No Link'
        
        # Menyimpan hasil dalam list
        all_results.append({
            'name': name,
            'address': address,
            'rating': rating,
            'link': link
        })
    
    # Mencari tombol "Next" untuk halaman selanjutnya
    try:
        next_button = driver.find_element(By.ID, 'pnnext')
        next_button.click()
        print("Next page found, scraping...")
        time.sleep(3)  # Beri waktu 3 detik untuk memuat halaman berikutnya
    except:
        # Jika tidak ada tombol "Next", berarti kita sudah di halaman terakhir
        print("No more pages found. Scraping finished.")
        break

# Menyimpan data ke dalam file CSV
with open('hospital_data_selenium.csv', mode='w', newline='', encoding='utf-8') as file:
    writer = csv.DictWriter(file, fieldnames=['name', 'address', 'rating', 'link'])
    writer.writeheader()  # Menulis header kolom
    
    # Menulis setiap hasil ke dalam file CSV
    for result in all_results:
        writer.writerow(result)

print("Data telah disimpan ke dalam 'hospital_data_selenium.csv'.")

# Tutup driver setelah selesai
driver.quit()
```

---

## 🎯 TIPS TAMBAHAN

### **Install Library:**
```bash
pip install selenium
pip install webdriver-manager
```

### **Jalankan Script:**
```bash
python scrape_hospital.py
```

### **Contoh Hasil CSV:**
```csv
name,address,rating,link
RSU Dr. Pirngadi,Medan,+100,+62611234567,https://rsupirngadi.com
RS Columbia Asia,Medan,+500,+62619876543,https://columbiaasia.com
RS Mitra Sejati,Medan,+300,+62614567890,https://mitrasejati.com
```

### **Cara Ganti Keyword Pencarian:**
Ganti bagian `q=rs+di+Sumatera+Utara` di URL dengan:
- `q=restoran+di+Jakarta` → scrape restoran
- `q=hotel+di+Bali` → scrape hotel
- `q=toko+kelontong+di+Bandung` → scrape toko

### **Mode Headless (Tanpa Browser Terbuka):**
Uncomment baris ini buat bikin lebih cepat:
```python
options.add_argument("--headless")
```

---

## ⚠️ IMPORTANT NOTES

1. **Jangan scrape terlalu cepat** — tambah `time.sleep(5)` atau lebih untuk hindari rate limiting
2. **Google bisa block IP** jika terdeteksi bot — gunakan proxy jika perlu
3. **Class name bisa berubah** — Google sering update HTML, jadi class seperti 'VkpGBb' mungkin berubah
4. **Untuk produksi**, tambahkan error handling yang lebih baik dan logging
5. **Hormati Terms of Service** — jangan gunakan untuk spam atau aktivitas ilegal

---

## 🔧 TROUBLESHOOTING

### **Error: "ChromeDriver not found"**
Pastikan udah install webdriver-manager:
```bash
pip install webdriver-manager
```

### **Error: "Element not found"**
Class name Google mungkin udah berubah. Inspect element di browser buat cari class name baru.

### **Script jalan tapi nggak nemu data**
- Tambah `time.sleep()` lebih lama (5-10 detik)
- Cek apakah website udah kebuka dengan benar
- Coba matikan ad blocker atau VPN

---

## 🎬 JUDUL & DESKRIPSI YOUTUBE (Clickbait Style)

**Judul:**  
CARA SCRAPE DATA RUMAH SAKIT DARI GOOGLE MAPS OTOMATIS! (Python + Selenium)

**Deskripsi:**  
Gue bakal kasih tau cara ambil data rumah sakit dari Google Maps—otomatis, tanpa manual copy-paste! Dalam video ini, lo bakal belajar:  
✅ Setup Python + Selenium + ChromeDriver  
✅ Scraping data rumah sakit di Sumatera Utara  
✅ Navigate otomatis ke halaman berikutnya  
✅ Export data ke CSV (Excel/Google Sheets)  
✅ Cara ganti keyword buat scrape restoran, hotel, dll  
✅ Tips & warning yang harus lo tau  

Tools yang dipake: Python + Selenium + webdriver-manager. 100% gratis & powerful!

#webscraping #python #selenium #datascience #tutorial #programming #automation
