# ChromeOS Brunch Builder via GitHub Actions

Workflow GitHub Actions ini digunakan untuk membuat file `chromeos.img` dari Brunch Framework dan ChromeOS Recovery Image langsung di cloud runner Ubuntu tanpa memerlukan VM Linux lokal.

---

## 🚀 Langkah-langkah Penggunaan

### 1. Buat Repository Baru di GitHub
1. Buka [GitHub New Repository](https://github.com/new).
2. Beri nama repository (misal: `brunch-builder`).
3. Pilih **Private** atau **Public**.
4. Klik **Create repository**.

---

### 2. Push Workflow ke Repository
Buka Terminal di folder ini dan jalankan perintah berikut:

```bash
git init
git add .gitignore .github README.md
git commit -m "feat: add brunch chromeos builder workflow"
git branch -M main
git remote add origin https://github.com/<USERNAME-ANDA>/<NAMA-REPO>.git
git push -u origin main
```

*(Catatan: File `.bin` dan `.img` lokal Anda sudah diabaikan oleh `.gitignore` sehingga tidak akan melebihi batas limit 100MB GitHub).*

---

### 3. Jalankan Build di GitHub Actions
1. Buka repository Anda di browser, lalu klik tab **Actions**.
2. Di menu sebelah kiri, pilih **"Build Brunch ChromeOS Image"**.
3. Klik tombol dropdown **"Run workflow"** di sebelah kanan.
4. Isi parameter:
   - **`recovery_url`**: Masukkan link download langsung ChromeOS Recovery Image dari Google / [cros.tech](https://cros.tech) (contoh: `https://dl.google.com/dl/edgedl/chromeos/recovery/chromeos_..._recovery.bin.zip`).
   - **`brunch_url`**: Biarkan default (Brunch r152) atau ganti dengan link rilis brunch lainnya.
   - **`image_size`**: Ukuran disk image (default: `14` GB).
   - **`compression`**: Pilih `7z` (ukuran file lebih kecil dan cepat diunduh).
   - **`create_release`**: Centang untuk otomatis membuat GitHub Release.
5. Klik **"Run workflow"**.

---

### 4. Download Hasil `chromeos.img`
Setelah proses build selesai (sekitar 5 - 10 menit):
- Buka halaman **Releases** di repository Anda, atau
- Scroll ke bagian bawah halaman workflow run pada bagian **Artifacts**.
- Download file `chromeos.img.7z` dan ekstrak di Mac Anda.
- Flash file `chromeos.img` ke USB drive menggunakan **BalenaEtcher** atau **Raspberry Pi Imager**.
