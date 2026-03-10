# Flora Music — Repo untuk PWABuilder APK

## Struktur File
```
├── index.html              ← Flora Music app
├── manifest.json           ← PWA Manifest
├── icons/
│   ├── icon-192.png
│   └── icon-512.png
└── .well-known/
    └── assetlinks.json     ← Isi setelah dapat SHA256 dari PWABuilder
```

## Langkah Build APK dari HP Android

### 1. Upload ke GitHub Pages
1. Buka **github.com** di Chrome HP
2. Login / daftar akun
3. Buat repo baru → nama: `flora-music` → Public
4. Upload semua file ini (termasuk folder `icons/` dan `.well-known/`)
5. Settings → Pages → Source: `main` branch → Save
6. Tunggu ~1 menit → URL akan muncul: `https://USERNAME.github.io/flora-music/`

### 2. Generate APK via PWABuilder
1. Buka **pwabuilder.com**
2. Masukkan URL GitHub Pages kamu
3. Klik **Start** → tunggu analisis selesai
4. Klik **Package for stores** → pilih **Android**
5. Isi:
   - Package ID: `com.USERNAME.floramusic`
   - App name: `Flora Music`
   - Signing: biarkan default (PWABuilder buatkan keystore)
6. Klik **Generate** → Download ZIP

### 3. Isi assetlinks.json
Setelah download ZIP dari PWABuilder:
1. Buka ZIP → cari file `signing-key-info.txt` atau lihat di halaman download
2. Salin nilai `SHA256 Certificate Fingerprint`
3. Edit `.well-known/assetlinks.json` di GitHub:
   - Ganti `GANTI_PACKAGE_NAME` → package ID yang kamu pilih
   - Ganti `GANTI_SHA256_DARI_PWABUILDER` → nilai SHA256 tadi
4. Commit perubahan → tunggu GitHub Pages update

### 4. Install APK
1. Aktifkan "Install dari sumber tidak dikenal" di pengaturan HP
2. Buka file APK dari ZIP PWABuilder
3. Install → buka Flora Music 🌿

## Catatan
- Flora mengakses file musik lokal via File System Access API
- TWA (Trusted Web Activity) berjalan di atas Chrome, jadi API ini tetap bekerja
- Pastikan Chrome versi 80+ terinstall di HP
