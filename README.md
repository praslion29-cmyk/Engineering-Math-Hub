Advanced Engineering Mathematics Study Hub
Aplikasi web satu file untuk belajar Matematika Teknik Lanjut dalam bahasa Indonesia. Tidak perlu instalasi, server, atau proses build: cukup buka file HTML di browser.
> Dibuat untuk mahasiswa teknik yang ingin benar-benar *memahami* rumus, bukan sekadar menghafal. Setiap rumus dilengkapi cara mengucapkan, arti tiap simbol, asal-usulnya, contoh angka, dan visualisasi interaktif.
Fitur
Materi dan penjelasan
12 modul (11 materi inti + Aerospace & Astrodinamika) dengan ringkasan, rumus (dirender dengan KaTeX), contoh soal, kesalahan umum, dan aplikasi teknik.
Diagram kartesius untuk setiap rumus (59 diagram) yang menggambarkan arti rumus secara visual, lengkap dengan keterangan cara membacanya.
Studi kasus teknik berangka di tiap modul, dari data sampai hasil.
Bedah rumus lengkap untuk 59 rumus: cara mengucapkan kata demi kata, arti tiap bagian, dan contoh angka yang bisa dicek sendiri.
Kamus simbol per modul dan halaman pencarian simbol gabungan (∂, ∇, ∮, Σ, λ, ζ, ωₙ, ℒ, σ, dan lainnya).
Asal-usul rumus: penurunan singkat, misalnya mengapa dA = r dr dθ atau mengapa ℒ{f′} = sF(s) − f(0).
Aplikasi di teknik yang rinci, dengan rumus pendukung.
Contoh soal bertahap dengan petunjuk yang bisa dibuka sebelum melihat jawaban lengkap.
Visualisasi interaktif
Visualisasi tertanam di setiap halaman modul: tab 2D dan 3D langsung di bawah rumus, lengkap dengan slider, angka yang dihitung langsung, dan keterangan rumus mana yang divisualisasikan.
Visualisasi 2D (16 scene): jumlah Riemann, garis potong ke singgung, dot/cross product, medan kemiringan dan Euler, potret fase, diagram Bode, pulsa dan spektrum Fourier, mode getar dawai, transformasi linear dan eigenvector, regresi kuadrat terkecil, pemetaan konformal, profil sayap Joukowski, Newton–Raphson, fenomena Runge, teorema limit pusat, dan pemrograman linear.
Visualisasi 3D (11 scene, satu per modul): permukaan dan bidang singgung, medan vektor, atraktor Lorenz (RK4), permukaan pole Laplace, heliks Fourier, permukaan panas/gelombang, kubus dan eigenvector, bola Riemann, kestabilan beda hingga, normal dua variabel, dan gradient descent. Seret kanvas untuk memutar.
Aerospace 3D: orbit Kepler (persamaan Kepler diselesaikan metode Newton), transfer Hohmann, dan sikap pesawat dengan matriks rotasi, lengkap dengan rumus kunci dan soal latihan.
Grafik dasar dengan satu slider (deret Fourier, respons orde-2, Taylor, Euler vs RK4, pole, aliasing).
Alat belajar
Quiz per modul (72 soal, pilihan ganda dan numerik) dengan pembahasan, plus mode ujian bertimer.
Alur Belajar: urutan modul yang disarankan, prasyarat, bar progres, dan peringatan bila prasyarat belum dikuasai.
Ekspor dan impor progres ke file `.json` untuk cadangan atau pindah perangkat.
Flashcard rumus dengan sisi belakang berisi cara membaca; tandai "Masih sulit" atau "Sudah hafal" agar kartu sulit lebih sering muncul.
Cheat sheet dengan pencarian, bookmark, dan tombol Cetak / simpan PDF.
Halaman Konstanta & Tabel: konstanta fisika, awalan SI, konversi satuan, dan tabel pasangan Laplace.
Pelacakan progres (subtopik selesai, skor quiz, catatan, bookmark, target harian) yang tersimpan di browser lewat `localStorage`.
Mode terang dan gelap.
Daftar modul
#	Modul
1	Kalkulus Lanjut
2	Kalkulus Vektor
3	Persamaan Diferensial Biasa
4	Transformasi Laplace
5	Deret & Transformasi Fourier
6	Persamaan Diferensial Parsial
7	Aljabar Linear
8	Analisis Kompleks
9	Metode Numerik
10	Probabilitas & Statistik
11	Optimasi
12	Aerospace & Astrodinamika
Cara menjalankan
Lokal
Unduh atau clone repositori ini.
Ganti nama file HTML menjadi `index.html`, lalu buka di browser.
```bash
git clone https://github.com/<username>/<nama-repo>.git
cd <nama-repo>
# buka index.html di browser
```
Lewat GitHub Pages
Pastikan file bernama `index.html` di root repositori.
Buka Settings → Pages.
Pada Source pilih branch `main` dan folder `/ (root)`, lalu simpan.
Situs tersedia di `https://<username>.github.io/<nama-repo>/`.
Catatan teknis
Seluruh aplikasi (HTML, CSS, JavaScript, dan data materi) ada dalam satu file.
Visualisasi 2D dan 3D digambar langsung dengan Canvas 2D dan proyeksi 3D buatan sendiri, tanpa library 3D tambahan.
Library eksternal dimuat lewat CDN, jadi dibutuhkan koneksi internet saat pertama membuka:
KaTeX untuk menampilkan rumus
Chart.js untuk grafik progres
Google Fonts (Newsreader dan Public Sans)
Data progres belajar disimpan hanya di browser Anda (`localStorage`, kunci `aem-hub-v1`). Tidak ada data yang dikirim ke server. Membersihkan data situs di browser akan menghapus progres.
Struktur data (untuk kontributor)
Materi didefinisikan sebagai objek JavaScript di dalam file HTML:
Variabel	Isi
`M`	Daftar modul: nama, warna, ringkasan, subtopik, rumus, contoh soal (`ex`), kesalahan umum (`err`), aplikasi (`app`)
`X`	Per modul: kamus simbol (`g`), ringkasan cara baca (`r`), aplikasi rinci (`a`)
`B`	Bedah rumus lengkap, kunci = nama rumus: `[cara mengucapkan, arti tiap bagian dipisah |, contoh angka]`
`D`	Asal-usul (penurunan) rumus per modul
`VZ`	Grafik dasar dengan satu slider
`V2S`, `V3S`	Scene visualisasi 2D dan 3D
Contoh menambah rumus baru:
```js
M[8].f.push(['Nama rumus', 'tampilan teks', '\\LaTeX{}']);

B['Nama rumus'] = [
  '"cara mengucapkan rumus"',
  'bagian 1 = arti|bagian 2 = arti|bagian 3 = arti',
  'Contoh angka singkat.'
];
```
Contoh menambah scene visualisasi 2D (fungsi `run` menggambar dan mengembalikan teks info):
```js
V2S.contoh = {
  m: 0,                 // indeks modul (warna dan label)
  t: 'Judul scene',
  p: [['a', 'Label slider', 0, 10, .1, 5]],   // [kunci, label, min, max, step, default]
  d: 'Penjelasan singkat apa yang dilihat.',
  run: (g, W, H, p) => {
    const h = one(g, W, H, [-5, 5, -5, 5]);   // jendela koordinat
    h.axes(1, 1); h.path(x => p.a * Math.sin(x), '#22d3ee', 2.6); h.frame();
    return `a = <b>${p.a}</b>`;
  }
};
```
Nama rumus di `B` harus sama persis dengan nama rumus di `M`.
Kontribusi
Kontribusi sangat diterima, terutama untuk:
Menambah soal quiz di modul yang bank soalnya masih sedikit (Kalkulus Lanjut, PDE, Metode Numerik, Probabilitas, Optimasi)
Menambah contoh soal bertingkat dan studi kasus teknik berangka
Menambah scene visualisasi 2D/3D baru
Memperbaiki salah ketik atau kesalahan rumus
Cara berkontribusi: fork repositori, buat branch baru, lakukan perubahan, lalu ajukan pull request dengan deskripsi singkat. Untuk koreksi rumus, sertakan referensinya.
Rencana pengembangan
[x] Bank soal quiz di semua modul (72 soal)
[ ] Perbanyak bank soal menjadi sekitar 10 per modul
[ ] Studi kasus teknik berangka satu per modul
[x] Panduan urutan belajar dan prasyarat per modul
[ ] Topik tambahan: distribusi binomial dan Poisson, uji hipotesis, kondisi KKT, integral kontur dan rumus integral Cauchy
[x] Visualisasi 2D dan 3D untuk setiap modul
[x] Bedah rumus lengkap, kamus simbol, asal-usul rumus
[x] Aplikasi aerospace dan astrodinamika
Disclaimer
Materi disusun untuk keperluan belajar. Periksa kembali rumus dan perhitungan dengan buku teks atau dosen pengampu sebelum dipakai untuk tugas, ujian, atau perancangan teknik nyata.
Lisensi
Pilih lisensi sesuai kebutuhan Anda, misalnya MIT, lalu tambahkan file `LICENSE` di repositori.
