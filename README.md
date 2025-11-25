# Project-1-nisaa
GAMBAR 1
https://drive.google.com/file/d/1MRAE2NTSbYpGH9QIo-wWcjBBxZG5n_sT/view?usp=drivesdk

touch report1.pdf

→ Membuat file kosong bernama report1.pdf
(jika sudah ada → memperbarui timestamp)

touch data2.xlsx

→ Membuat file kosong bernama data2.xlsx

touch pdf_minggu_lalu.txt

→ Membuat file kosong bernama pdf_minggu_lalu.txt

 Ketiga perintah touch di atas digunakan untuk membuat beberapa file contoh (PDF, XLSX, TXT)

mkdir -p server/marketing/documents server/marketing/archives

atau pada bagian lain terlihat:

mkdir -p server/documents server/archives

Penjelasan:

mkdir → Membuat folder (directory)

-p → Membuat seluruh struktur folder sekaligus tanpa error jika folder sudah ada

Dibuat beberapa folder bersarang di dalam folder server

 Struktur folder yang dibuat:

server
└── marketing
    ├── documents
    └── archives

Folder-folder ini akan digunakan untuk mengelola file perusahaan, misalnya file marketing.

Kesimpulan Sederhana

Perintah	Fungsi

touch	Membuat file: report PDF, file Excel, dan file TXT
mkdir -p	Membuat beberapa folder sekaligus dalam struktur bertingkat

GAMBAR 2
https://drive.google.com/file/d/1idbspN6z8FHUnsPwLf5xLPQ_IiO32kQn/view?usp=drivesdk

 Membuat struktur folder

mkdir -p server/marketing/documents server/marketing/archives
mkdir -p server/engineering/documents server/engineering/archives
mkdir -p server/hr/documents server/hr/archives

Fungsi:

mkdir → membuat folder

-p → membuat struktur folder bersarang sekaligus


 Hasil struktur direktori:

server
├── marketing
│   ├── documents
│   └── archives
├── engineering
│   ├── documents
│   └── archives
└── hr
    ├── documents
    └── archives

 Memindahkan file ke folder yang sesuai

mv report1.pdf server/marketing/documents/

→ Memindahkan report1.pdf ke folder marketing/documents

mv data2.xlsx server/engineering/documents/

→ Memindahkan data2.xlsx ke folder engineering/documents

 mv bisa digunakan untuk memindahkan atau mengganti nama file

 Menyalin file untuk arsip

cp server/marketing/documents/report1.pdf server/marketing/archives/

→ Menyalin report1.pdf ke folder archives sebagai arsip

cp server/engineering/documents/data2.xlsx server/engineering/archives/

→ Menyalin data2.xlsx ke folder engineering/archives

 cp digunakan untuk meng-copy file tanpa memindahkan aslinya

 Membuat grup baru

sudo groupadd marketing

→ Membuat grup marketing di sistem Linux
(sudo = hak administrator) 

 Kesimpulan Aktivitas di Gambar

Tahap	Kegiatan

✓ Struktur folder dibuat	Folder untuk marketing, engineering, hr
✓ File ditempatkan	PDF ke marketing, XLSX ke engineering
✓ Arsip dibuat	Dengan perintah cp
✓ Permission disiapkan	Grup marketing dibuat

GAMBAR 3
https://drive.google.com/file/d/1h_uK2hlWbSiUfZmrFP-MNBIbiSpLEtIh/view?usp=drivesdk

 Mengubah pemilik (owner) folder secara rekursif

sudo chown -R marketing server/marketing
sudo chown -R engineering server/engineering
sudo chown -R hr server/hr

Penjelasan:

sudo → menjalankan sebagai administrator

chown → mengubah ownership

-R → recursive, semua isi folder ikut berubah

Grup atau user yang jadi pemilik:

Folder marketing → grup marketing

Folder engineering → grup engineering

Folder hr → grup hr

 Tujuan: Folder hanya bisa dikelola oleh departemen yang tepat

 Memberi hak akses (permission) pada folder

sudo chmod -R 770 server/marketing
sudo chmod -R 770 server/engineering
sudo chmod -R 770 server/hr

Penjelasan kode 770:

Akses	User	Group	Other

7	rwx	7	rwx

 Hanya pemilik & grup yang bisa: √ Melihat isi folder
√ Mengedit file
√ Menjalankan file
❌ Orang luar tidak punya akses

 Mencari file PDF di dalam folder server

find server -name "*.pdf"

→ Menampilkan semua file berformat .pdf di dalam folder server

 Mencari PDF yang dimodifikasi dalam 7 hari terakhir

find server -name "*.pdf" -mtime -7

Keterangan:

-mtime -7 → file yang dibuat / diubah kurang dari 7 hari

 Ini cocok digunakan untuk backup file terbaru

 Mencari PDF terbaru dan file bernama pdf_minggu_lalu.txt

find server -name "*.pdf" -mtime -7 -o -name "pdf_minggu_lalu.txt"

Penjelasan logika:

-o = OR (atau)

Jadi file yang muncul adalah: √ Semua PDF terbaru
√ File pdf_minggu_lalu.txt meskipun lebih lama dari 7 hari

 Rangkuman Fungsi Semua Perintah

Kategori	Perintah	Fungsinya

Manajemen Hak Akses	chown	Menentukan pemilik folder sesuai departemen
	chmod 770	Mengunci akses folder agar aman
Pencarian File	find	Memfilter file berdasarkan jenis & umur file

 Kesimpulan

Perintah-perintah ini digunakan untuk:

√ Mengelola keamanan & akses file perusahaan
√ Mengatur kepemilikan berdasarkan departemen
√ Menyeleksi file yang akan dibackup (PDF terbaru)
