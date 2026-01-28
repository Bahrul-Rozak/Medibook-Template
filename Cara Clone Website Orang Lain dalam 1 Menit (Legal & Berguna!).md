# JUDUL: Cara Clone Website Orang Lain dalam 1 Menit (Legal & Berguna!)

**Durasi:** 200 detik  
**Gaya:** Storytelling teknis dengan bahasa santai, mudah dipahami pemula

---

## 📋 BREAKDOWN DETIK-DEMI-DETIK

### **HOOK (0–15 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 0–5 | Lo pernah kepikiran nggak... gimana cara download seluruh website orang—jadiin offline? | Tunjuk website di laptop |
| 6–10 | Bukan buat hack ya! Tapi buat backup, belajar, atau riset kompetitor. | Angkat tangan "tenang bro" |
| 11–15 | Nah, hari ini gue bakal kasih tau cara legal clone website dalam 1 menit aja. | Senyum, jari tunjuk layar |

---

### **CHAPTER 1: Apa Itu Web Scraping? (15–50 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 15–22 | Web scraping itu kayak... fotokopi digital. Lo ambil semua konten website—HTML, CSS, gambar, JS—terus simpen di komputer lo. | Gesture "ambil dan simpan" |
| 23–30 | Bedanya sama Ctrl+S? Kalau Ctrl+S cuma halaman satu. Scraping bisa ambil SEMUA halaman—recursive, bro! | Tunjuk banyak tab browser |
| 31–38 | Dan yang paling keren: ini 100% legal selama lo nggak buat hal jahat. Buat belajar, backup, atau analisis—boleh banget. | Jempol ke atas |
| 39–45 | Tools yang kita pake namanya `website-scraper`—library Node.js yang bikin scraping jadi gampang banget. | Tunjuk code editor |
| 46–50 | *(jeda napas)* | Ambil napas, minum air |

---

### **CHAPTER 2: Setup Awal — Install Library (50–90 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 50–58 | Pertama, lo harus punya Node.js udah terinstall. Belum? Download di nodejs.org—gratis. | Tunjuk website nodejs.org |
| 59–66 | Lalu buka terminal atau CMD, masuk ke folder project lo. Gue biasanya bikin folder baru namanya "scraper-project". | Ketik di terminal: `mkdir scraper-project` |
| 67–75 | Terus install library-nya pake perintah: `npm install website-scraper` —tunggu beberapa detik sampai selesai. | Ketik: `npm install website-scraper` |
| 76–83 | Kalau udah, buat file baru namanya `scraper.js`. Bisa pake VS Code, Sublime, atau Notepad++—bebas. | Buka code editor, buat file baru |
| 84–90 | *(jeda napas)* | Stretch tangan sebentar |

---

### **CHAPTER 3: Breakdown Kode — Baris demi Baris (90–170 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 90–97 | Oke, sekarang kita bahas kode-nya. Baris pertama: `import scrape from 'website-scraper'` —ini buat import library yang tadi udah kita install. | Highlight baris 1 di code |
| 98–105 | Baris kedua: `const websiteUrl = 'https://bahrul-rozak.vercel.app/'` —ini target website yang mau kita clone. Ganti sama URL lo sendiri. | Highlight baris 2 |
| 106–115 | Nah, bagian paling seru ada di sini—fungsi `scrape()` dengan konfigurasi di dalamnya. Ini otaknya. | Zoom in ke fungsi scrape |
| 116–123 | `urls: [websiteUrl]` —daftar website yang mau di-scrape. Bisa lebih dari satu, tinggal tambah koma terus URL baru. | Tunjuk array urls |
| 124–132 | `urlFilter` —ini penting! Fungsinya biar scraping nggak nyasar ke website lain. Cuma ambil yang domain-nya sama. | Gesture "stay in lane" |
| 133–140 | `recursive: true` —ini yang bikin ajaib. Kalau true, scraper bakal ikutin semua link di website itu. Dari homepage ke about, ke blog, ke contact—semua! | Gesture rantai/link |
| 141–148 | `maxDepth: 50` —batas kedalaman link. Angka 50 artinya scraper boleh masuk 50 level link berturut-turut. Kalau website lo cuma 5 halaman, ganti jadi 5 aja biar cepet. | Tunjuk angka 50 |
| 149–156 | `prettifyUrls: true` —biar URL hasil download rapih, nggak acak-acakan. Gampangnya: URL jadi folder structure yang enak dilihat. | Gesture "rapih" |
| 157–164 | `filenameGenerator: 'bySiteStructure'` —ini bikin file hasil download nyusun kayak struktur website aslinya. Blog jadi folder blog, images jadi folder images. | Tunjuk struktur folder |
| 165–170 | `directory: './result'` —tempat semua file hasil scraping disimpan. Nanti bakal muncul folder "result" di project lo. | Highlight path './result' |

---

### **CHAPTER 4: Jalankan & Lihat Hasilnya! (170–210 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 170–178 | Oke, kode udah siap. Sekarang tinggal jalanin! Buka terminal, ketik: `node scraper.js` —enter! | Ketik di terminal |
| 179–186 | Tunggu beberapa detik sampai muncul tulisan "Entire website successfully downloaded". Artinya... berhasil! | Tunggu loading, senyum |
| 187–195 | Cek folder project lo—sekarang ada folder baru namanya "result". Di dalamnya? SEMUA file website itu: HTML, CSS, JS, gambar—semua! | Buka folder result di explorer |
| 196–203 | Lo bisa buka file index.html-nya langsung di browser—website itu bakal jalan offline, tanpa internet! | Double click index.html |
| 204–210 | *(jeda napas)* | Tatap kamera, ekspresi "keren kan?" |

---

### **CHAPTER 5: Use Cases — Buat Apa Sih Ini? (210–250 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 210–217 | "Terus... buat apa sih clone website orang?" Pertanyaan bagus! Ini beberapa use case-nya: | Hitung pakai jari |
| 218–225 | **Pertama: Backup website.** Kalau website lo atau klien tiba-tiba down atau kena hack, lo punya copy lengkap di komputer. | Gesture "save" |
| 226–233 | **Kedua: Belajar dari website orang.** Pengen tau gimana website keren dibangun? Clone, terus pelajari source code-nya! | Gesture "belajar" |
| 234–241 | **Ketiga: Riset kompetitor.** Analisis struktur website kompetitor—lihat gambar apa yang mereka pake, konten apa yang populer. | Gesture "analisis" |
| 242–247 | **Keempat: Archiving.** Simpen website penting yang mungkin suatu hari bakal ilang dari internet. | Gesture "arsip" |
| 248–250 | *(jeda napas)* | Angguk pelan |

---

### **CHAPTER 6: Warning & Etika (250–280 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 250–258 | TAPI—ada beberapa hal yang harus lo inget. Pertama: jangan scrape website yang punya anti-bot atau CAPTCHA. Nanti error. | Gesture "stop" |
| 259–266 | Kedua: jangan gunain buat hal ilegal—spam, phising, atau nyolong konten buat dijual lagi. Etika, bro! | Ekspresi serius |
| 267–274 | Ketiga: jangan scrape website pemerintah atau yang sensitif. Bisa kena masalah legal. | Geleng kepala |
| 275–280 | Intinya: pakai dengan bijak. Teknologi itu netral—yang bedain adalah niat lo pake buat apa. | Tatap kamera, nada tegas |

---

### **CLOSING & CALL TO ACTION (280–300 detik)**

| Waktu | Narasi | Visual |
|-------|--------|--------|
| 280–287 | Jadi... sekarang lo udah tau cara clone website orang dalam 1 menit. Gampang kan? | Senyum |
| 288–293 | Coba praktekin sendiri—ambil website portfolio lo atau website tutorial favorit lo. | Gesture "coba sekarang" |
| 294–298 | Kalau berhasil, komen di bawah! Share juga website apa yang lo clone—siapa tau bisa jadi referensi buat yang lain. | Tunjuk kolom komentar |
| 299–300 | Sampai jumpa di video berikutnya! | Wave tangan |

---

## 📝 FULL CODE YANG SUDAH DIJELASKAN

```javascript
import scrape from 'website-scraper';

// Target website yang mau di-scrape
const websiteUrl = 'https://bahrul-rozak.vercel.app/';

scrape({
    // URL website yang mau diambil
    urls: [websiteUrl],
    
    // Filter biar nggak nyasar ke domain lain
    urlFilter: function (url) {
        return url.indexOf(websiteUrl) === 0;
    },
    
    // Ambil semua link di dalam website (rekursif)
    recursive: true,
    
    // Maksimal kedalaman link yang diikuti
    maxDepth: 50,
    
    // Bikin URL jadi rapih
    prettifyUrls: true,
    
    // Struktur folder nyusun kayak website asli
    filenameGenerator: 'bySiteStructure',
    
    // Tempat simpan hasil scraping
    directory: './result'
    
}).then((data) => {
    // Kalau berhasil
    console.log("Entire website succesfully downloaded");
    
}).catch((err) => {
    // Kalau error
    console.log("An error ocurred", err);
});
```

---

## 🎯 TIPS TAMBAHAN

### **Install Library:**
```bash
npm install website-scraper
```

### **Jalankan Script:**
```bash
node scraper.js
```

### **Kalau Pakai CommonJS (Node.js lama):**
```javascript
const scrape = require('website-scraper');
```

### **Contoh Hasil Folder Structure:**
```
result/
├── index.html
├── about/
│   └── index.html
├── blog/
│   ├── post-1.html
│   └── post-2.html
├── css/
│   └── style.css
├── js/
│   └── script.js
└── images/
    ├── logo.png
    └── banner.jpg
```

---

## ⚠️ IMPORTANT NOTES

1. **Pastikan website target mengizinkan scraping** (cek `robots.txt`)
2. **Jangan gunakan untuk website berbayar/subscription**
3. **Hormati copyright**—jangan publish ulang konten orang tanpa izin
4. **Untuk website besar**, kurangi `maxDepth` biar nggak lama

---

## 🎬 JUDUL & DESKRIPSI YOUTUBE (Clickbait Style)

**Judul:**  
CARA CLONE WEBSITE ORANG DALAM 1 MENIT! (Legal & Berguna!)

**Deskripsi:**  
Gue bakal kasih tau cara download seluruh website orang—jadiin offline di komputer lo! Bukan buat hack ya, tapi buat backup, belajar, atau riset kompetitor. Dalam video ini, lo bakal belajar:  
✅ Install library website-scraper  
✅ Setup konfigurasi scraping  
✅ Jalankan script & lihat hasilnya  
✅ Use cases yang berguna (backup, belajar, riset)  
✅ Etika & warning yang harus lo tau  

Tools yang dipake: Node.js + website-scraper library. 100% legal selama dipake dengan bijak!

#webscraping #webdevelopment #javascript #tutorial #programming #nodejs
