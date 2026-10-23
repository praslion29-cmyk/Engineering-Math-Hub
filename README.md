# Advanced Engineering Mathematics Study Hub

Aplikasi web satu file untuk belajar **Matematika Teknik Lanjut** dalam bahasa Indonesia. Tidak perlu instalasi, tidak perlu server, dan tidak ada proses build: cukup buka file HTML di browser.

> Dibuat untuk mahasiswa teknik yang ingin benar-benar *memahami* rumus, bukan sekadar menghafal. Setiap rumus dilengkapi cara mengucapkan, arti tiap simbol, asal-usulnya, dan contoh angka.

## Fitur

**Materi dan penjelasan**
- 11 modul dengan ringkasan, rumus (dirender dengan KaTeX), contoh soal, kesalahan umum, dan aplikasi teknik.
- **Bedah rumus lengkap** untuk 50 rumus: cara mengucapkan kata demi kata, arti tiap bagian, dan contoh angka yang bisa dicek sendiri.
- **Kamus simbol** per modul dan halaman pencarian simbol gabungan (∂, ∇, ∮, Σ, λ, ζ, ωₙ, ℒ, σ, dan lainnya).
- **Asal-usul rumus**: penurunan singkat, misalnya mengapa dA = r dr dθ atau mengapa ℒ{f′} = sF(s) − f(0).
- **Aplikasi di teknik** yang rinci, dengan rumus pendukung (getaran, rangkaian RLC, kontrol, FEM, kendali mutu, dan lain-lain).
- Contoh soal bertahap dengan **petunjuk** yang bisa dibuka sebelum melihat jawaban lengkap.

**Alat belajar**
- Quiz per modul dengan pembahasan.
- Flashcard rumus: balik kartu untuk melihat rumus dan cara membacanya, tandai **"Masih sulit"** atau **"Sudah hafal"** agar kartu sulit lebih sering muncul.
- Cheat sheet dengan pencarian, bookmark, dan tombol **Cetak / simpan PDF**.
- Halaman **Konstanta & Tabel**: konstanta fisika, awalan SI, konversi satuan, dan tabel pasangan Laplace.
- Visualisasi interaktif dengan slider: deret Fourier gelombang persegi, respons step orde 2, deret Taylor sin x, Euler vs Runge–Kutta 4, letak pole dan respons waktu, serta aliasing dan teorema Nyquist.
- Pelacakan progres (subtopik selesai, skor quiz, catatan, bookmark, target harian), tersimpan di browser lewat `localStorage`.
- Mode terang dan gelap.

## Daftar modul

| # | Modul |
|---|-------|
| 1 | Kalkulus Lanjut |
| 2 | Kalkulus Vektor |
| 3 | Persamaan Diferensial Biasa |
| 4 | Transformasi Laplace |
| 5 | Deret & Transformasi Fourier |
| 6 | Persamaan Diferensial Parsial |
| 7 | Aljabar Linear |
| 8 | Analisis Kompleks |
| 9 | Metode Numerik |
| 10 | Probabilitas & Statistik |
| 11 | Optimasi |

## Cara menjalankan

**Lokal**

1. Unduh atau clone repositori ini.
2. Buka `index.html` (atau nama file HTML yang Anda pakai) langsung di browser.

```bash
git clone https://github.com/<username>/<nama-repo>.git
cd <nama-repo>
# lalu buka file HTML di browser
```

**Lewat GitHub Pages**

1. Ganti nama file menjadi `index.html`.
2. Di repositori, buka **Settings → Pages**.
3. Pada *Source* pilih branch `main` dan folder `/ (root)`, lalu simpan.
4. Situs akan tersedia di `https://<username>.github.io/<nama-repo>/`.

## Catatan teknis

- Seluruh aplikasi (HTML, CSS, JavaScript, dan data materi) ada dalam **satu file**.
- Library eksternal dimuat lewat CDN, jadi dibutuhkan koneksi internet saat pertama membuka:
  - [KaTeX](https://katex.org/) untuk menampilkan rumus
  - [Chart.js](https://www.chartjs.org/) untuk grafik progres
  - Google Fonts (Newsreader dan Public Sans)
- Data progres belajar disimpan **hanya di browser Anda** (`localStorage`, kunci `aem-hub-v1`). Tidak ada data yang dikirim ke server mana pun. Membersihkan data situs di browser akan menghapus progres.

## Struktur data (untuk kontributor)

Materi didefinisikan sebagai array JavaScript di dalam file HTML:

| Variabel | Isi |
|----------|-----|
| `M` | Daftar modul: nama, warna, ringkasan, subtopik, rumus, contoh soal (`ex`), kesalahan umum (`err`), aplikasi (`app`) |
| `X` | Per modul: kamus simbol (`g`), ringkasan cara baca (`r`), aplikasi rinci (`a`) |
| `B` | Bedah rumus lengkap, dengan kunci berupa nama rumus: `[cara mengucapkan, arti tiap bagian dipisah \|, contoh angka]` |
| `D` | Asal-usul (penurunan) rumus per modul |
| `VZ` | Definisi visualisasi interaktif |

Contoh menambah rumus baru di modul tertentu:

```js
M[8].f.push(['Nama rumus', 'tampilan teks', '\\LaTeX{}']);

B['Nama rumus'] = [
  '"cara mengucapkan rumus"',
  'bagian 1 = arti|bagian 2 = arti|bagian 3 = arti',
  'Contoh angka singkat.'
];
```

Nama rumus di `B` harus sama persis dengan nama rumus di `M`.

## Kontribusi

Kontribusi sangat diterima, terutama untuk:

- Menambah soal quiz di modul yang bank soalnya masih sedikit (Kalkulus Lanjut, PDE, Metode Numerik, Probabilitas, Optimasi)
- Menambah contoh soal bertingkat dan studi kasus teknik berangka
- Menambah visualisasi interaktif baru
- Memperbaiki salah ketik atau kesalahan rumus

Cara berkontribusi: *fork* repositori, buat branch baru, lakukan perubahan, lalu ajukan *pull request* dengan deskripsi singkat. Untuk koreksi rumus, sertakan referensinya.

## Rencana pengembangan

- [ ] Bank soal quiz untuk semua modul (target sekitar 10 soal per modul)
- [ ] Studi kasus teknik berangka satu per modul
- [ ] Visualisasi: medan vektor dan gradient, transformasi eigenvector 2D, spektrum FFT
- [ ] Panduan urutan belajar dan prasyarat per modul
- [ ] Topik tambahan: distribusi binomial dan Poisson, uji hipotesis, linear programming, kondisi KKT, integral kontur dan rumus integral Cauchy

## Disclaimer

Materi disusun untuk keperluan belajar. Periksa kembali rumus dan perhitungan dengan buku teks atau dosen pengampu sebelum dipakai untuk tugas, ujian, atau perancangan teknik nyata.

## Lisensi

Pilih lisensi sesuai kebutuhan Anda, misalnya [MIT](https://choosealicense.com/licenses/mit/), lalu tambahkan file `LICENSE` di repositori.
