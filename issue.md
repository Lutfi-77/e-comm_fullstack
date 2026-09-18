# Prompt: Frontend E-Commerce (Next.js + JavaScript) — Buyer + Seller Dashboard

> Copy-paste seluruh prompt di bawah ini ke AI coding tool kamu (Claude Code, Cursor, v0, bolt.new, dll).

---

## PROMPT

Buatkan **frontend UI lengkap untuk aplikasi e-commerce** menggunakan **Next.js (App Router) + JavaScript (JSX, BUKAN TypeScript)** dan **Tailwind CSS**. Ini murni project **tampilan (UI-only)**. Fokus 100% ke visual dan layout — **tidak perlu ada logika fungsional nyata sama sekali**: tombol "Tambah ke Keranjang", "Checkout", "Update Status Pesanan", dsb cukup ada secara visual (boleh non-fungsional / tanpa `onClick` yang mengubah apa pun), karena backend dan semua logika akan saya bangun sendiri sambil belajar menggunakan Node.js + Express.

### Tech Stack

- Next.js 15 (App Router) — **gunakan file `.js` / `.jsx`, jangan `.ts` / `.tsx`**
- Tailwind CSS
- shadcn/ui untuk komponen dasar (button, dialog, dropdown, table, tabs, badge, dll) — pastikan versi komponennya dalam JavaScript, bukan TypeScript
- lucide-react untuk icon
- recharts untuk grafik/statistik di dashboard seller
- Boleh pakai free admin dashboard template (misal Shadcn Admin, TailAdmin, Horizon UI Free, Materio Free) sebagai basis dashboard seller, port ke JavaScript dan sesuaikan style-nya dengan sisi user supaya konsisten satu brand.

### Struktur Folder yang Diinginkan

```
/app
  /(shop)                → semua halaman untuk pembeli (user)
    /page.jsx            → homepage
    /products
    /products/[id]
    /cart
    /checkout
    /orders
    /orders/[id]/track   → halaman tracking pesanan
    /wishlist
    /profile
    /login
    /register
  /(seller)
    /dashboard
      /overview
      /products
      /products/new
      /products/[id]/edit
      /orders
      /orders/[id]
      /inventory
      /settings
      /reviews
/components
  /shop        → komponen sisi pembeli
  /dashboard   → komponen sisi seller
  /shared      → navbar, footer, komponen umum
/data          → semua dummy data (products.js, orders.js, users.js, sellers.js, reviews.js)
```

Semua file JavaScript murni (`.js`/`.jsx`), tanpa anotasi tipe TypeScript, tanpa interface, tanpa `.d.ts`.

---

### 1. SISI PEMBELI (User / Buyer)

**Halaman Home**

- Hero section dengan banner promo (carousel/slider, boleh statis)
- Section kategori produk (grid icon/kategori)
- Section produk unggulan / flash sale (dengan tampilan countdown timer visual, tidak perlu berjalan real-time)
- Section produk terbaru
- Footer lengkap (info, kategori, sosial media, newsletter)

**Halaman Katalog Produk**

- Grid produk dengan filter sidebar (kategori, harga, rating, brand) — tampilan saja, tidak perlu filtering benar-benar berfungsi
- Sorting UI (termurah, termahal, terlaris, terbaru)
- Pagination (tampilan saja)
- Search bar (tampilan saja, tidak perlu logic pencarian)

**Halaman Detail Produk**

- Galeri gambar produk (multiple images dummy)
- Info produk, harga, varian (ukuran/warna), stok
- Tombol "Tambah ke Keranjang" & "Beli Sekarang" (visual saja, tanpa aksi)
- Tab: Deskripsi, Spesifikasi, Ulasan (review + rating dengan dummy data)
- Section "Produk Serupa"

**Keranjang (Cart)**

- Tampilkan beberapa item dummy dengan qty, harga
- Ringkasan harga (subtotal, ongkir dummy, diskon, total) — angka dummy statis
- Tampilan tombol checkout (tidak perlu berfungsi)

**Checkout**

- Form alamat pengiriman (tampilan form saja, isi dummy)
- Pilihan metode pengiriman (dummy: reguler/express dengan estimasi harga & waktu)
- Pilihan metode pembayaran (dummy: transfer bank, e-wallet, COD) — tampilan saja
- Ringkasan pesanan final (data dummy statis)

**Riwayat & Tracking Pesanan**

- List beberapa pesanan dummy (status: Menunggu Pembayaran, Diproses, Dikirim, Selesai, Dibatalkan)
- **Halaman detail tracking per pesanan** dengan timeline visual step-by-step (data statis, tidak perlu logic):
  - Pesanan Dibuat → Dikonfirmasi Penjual → Dikemas → Diserahkan ke Kurir → Dalam Perjalanan → Tiba di Kota Tujuan → Sedang Diantar → Selesai
  - Tampilkan waktu di tiap step, nomor resi dummy, nama kurir dummy
  - Progress bar horizontal/vertikal dengan icon di tiap tahap (posisi progress cukup hardcode sesuai contoh, tidak perlu dinamis)

**Wishlist** — grid produk dummy yang "disimpan"

**Profil User** — info akun dummy, alamat dummy, riwayat transaksi ringkas

**Login/Register** — form UI saja, tanpa validasi maupun logic apa pun

---

### 2. SISI PENJUAL (Seller Dashboard)

Gunakan layout admin dashboard (sidebar + topbar), boleh mengadaptasi dari template gratis yang disebutkan di atas (port ke JavaScript), tapi pastikan konsisten dengan tema warna sisi user.

**Overview / Analytics**

- Card statistik: total penjualan, total pesanan, produk terjual, pengunjung toko (angka dummy statis)
- Grafik penjualan (line/bar chart per hari/minggu/bulan) pakai recharts dengan data dummy
- Tabel pesanan terbaru (dummy)
- Widget produk terlaris (dummy)

**Manajemen Produk**

- Tabel produk dummy (gambar, nama, kategori, harga, stok, status aktif/nonaktif) dengan tampilan search & filter (tidak perlu berfungsi)
- Form tambah/edit produk (tampilan form lengkap, tidak perlu submit logic)
- Tombol bulk action (tampilan saja)

**Manajemen Pesanan**

- Tabel pesanan dummy dengan status & filter status (tampilan saja)
- Detail pesanan: info pembeli dummy, produk dipesan, alamat pengiriman
- Tampilan dropdown/step untuk "update status pesanan" — cukup visual, tidak perlu benar-benar mengubah state atau terhubung ke halaman tracking user
- Input nomor resi & pilih kurir (tampilan form saja)

**Inventori** — tabel stok produk dummy, badge alert stok menipis

**Reviews** — list ulasan dummy dari pembeli, tampilan tombol balas ulasan (tanpa logic)

**Settings** — form profil toko, jam operasional, metode pembayaran, info rekening (semua dummy, tampilan saja)

---

### 3. Kebutuhan Desain (Wajib Diikuti — Supaya Tidak Flat)

- **Jangan pakai default Tailwind polos** (grey-100/blue-500 generik). Tentukan **satu palet warna brand yang jelas** (primary, secondary, accent) dan pakai konsisten di semua halaman.
- Gunakan **shadow lembut**, **border-radius besar (rounded-xl/2xl)**, dan **spacing yang lega**, bukan garis pembatas abu-abu tipis.
- Tambahkan **micro-interaction visual**: hover state, transition halus (150–300ms), skeleton loading (boleh statis/dekoratif).
- Gunakan **empty state** yang menarik (ilustrasi/icon) untuk contoh cart kosong, wishlist kosong, dsb — bukan teks polos.
- Responsive penuh: mobile, tablet, desktop.
- Sediakan mode terang (light) sebagai default; dark mode opsional jika sempat.
- Gunakan font selain default sistem (misal Inter, Plus Jakarta Sans, atau Poppins dari Google Fonts) untuk kesan lebih premium.
- Semua gambar produk boleh pakai placeholder dari `https://picsum.photos` atau ilustrasi (undraw/unsplash) — konsisten ukuran & rasio.

---

### 4. Dummy Data

Buat minimal, semua ditulis sebagai file JavaScript biasa (array of object, tanpa tipe):

- 20–30 produk dummy (beda kategori, harga, gambar, rating, stok) → `/data/products.js`
- 10–15 pesanan dummy dengan status berbeda-beda (mencakup semua tahap tracking) → `/data/orders.js`
- 3–5 seller dummy → `/data/sellers.js`
- 5–10 user dummy → `/data/users.js`
- Review dummy untuk beberapa produk → `/data/reviews.js`

Import data ini langsung ke komponen untuk ditampilkan (tanpa fetch, tanpa API, tanpa state management kompleks — cukup render langsung dari array dummy).

---

### 5. Catatan Penting untuk AI

- Ini **UI-only, murni tampilan**. Jangan buat backend, API route Next.js, database, atau file konfigurasi environment.
- **Jangan tulis logic fungsional apa pun** — tidak perlu state management untuk cart, tidak perlu simulasi login berhasil/gagal, tidak perlu filter/sort yang benar-benar bekerja, tidak perlu update status pesanan yang benar-benar berubah. Semua tombol dan interaksi cukup ada secara visual.
- **Jangan gunakan TypeScript sama sekali** — semua file `.js`/`.jsx`, tanpa `interface`, `type`, atau anotasi tipe.
- **Jangan tambahkan komentar placeholder untuk backend/API** (seperti `// TODO: connect to API`) — biarkan halaman sepenuhnya berdiri sendiri dengan dummy data.
- Prioritaskan tampilan yang **menarik secara visual** dan **konsisten** di seluruh halaman, karena fokus utama project ini adalah UI.
