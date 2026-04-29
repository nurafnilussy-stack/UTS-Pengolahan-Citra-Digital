# UTS-Pengolahan-Citra-Digital
================================================================================
ANALISIS SOAL NO.1 - TRANSFORMASI CITRA GRAYSCALE
================================================================================

1. PERBEDAAN PERSEBARAN NILAI KEABUAN

Berdasarkan histogram yang dihasilkan:

a) Citra Asli:
   Histogram menunjukkan distribusi nilai keabuan asli dari citra.
   Bentuk histogram tergantung pada kontras dan pencahayaan citra.

b) Citra Negatif (G = 255 - F):
   Histogram merupakan cerminan horizontal dari histogram asli.
   Nilai 0 menjadi 255, nilai 255 menjadi 0.
   Persebaran nilai tetap linear dan menjangkau seluruh rentang 0-255.
   Jika asli dominan gelap, maka negatif akan dominan terang.

c) Citra Logaritmik (G = c × log(1+F)):
   Histogram bergeser ke kanan (nilai lebih tinggi) dibanding asli.
   Daerah gelap (nilai rendah) mengalami penguatan (stretching).
   Daerah terang (nilai tinggi) mengalami kompresi.
   Efek: detail di area gelap menjadi lebih terlihat.

2. KAPAN TRANSFORMASI LOGARITMIK LEBIH BERMANFAAT DARI NEGATIF?

Transformasi logaritmik lebih bermanfaat daripada negatif pada kasus:

✓ Citra dengan rentang dinamis sangat lebar (wide dynamic range)
  Contoh: foto dengan latar belakang sangat terang dan objek depan gelap.
  Logaritmik dapat menampilkan detail di kedua area sekaligus,
  sedangkan negatif hanya membalik tanpa mengatasi masalah rentang.

✓ Citra underexposed (terlalu gelap) yang memiliki detail penting
  Contoh: foto malam hari, foto di dalam ruangan minim cahaya,
  foto bawah air, atau citra medis (X-ray).
  Logaritmik memperkuat area gelap dan memperlihatkan detail tersembunyi.

✓ Visualisasi spektrum Fourier (magnitude spectrum)
  Logaritmik digunakan untuk menekan puncak yang sangat tinggi
  dan menonjolkan komponen frekuensi kecil.

Sebaliknya, transformasi negatif lebih bermanfaat untuk:
- Membalik persepsi latar depan dan latar belakang
- Mendeteksi objek terang pada latar gelap (atau sebaliknya)
- Preparasi sebelum operasi morfologi (dilation/erosion)

3. KESIMPULAN

Kedua transformasi memiliki tujuan berbeda:
- Negatif: transformasi LINEAR untuk membalik nilai keabuan
- Logaritmik: transformasi NON-LINEAR untuk memperkuat area gelap

Pemilihan tergantung pada kebutuhan analisis citra.

================================================================================
Dibuat untuk UTS Pengolahan Citra Digital
Tanggal: 28 April 2026
================================================================================









Jawaban 2
1. Perbandingan Visual dan Nilai Piksel Rata-rataBerdasarkan hasil eksekusi program pada citra singa, didapatkan perbandingan sebagai berikut:Low Pass Filter (LPF):Visual: Citra tampak lebih halus (blur). Detail tajam seperti helai bulu singa dan tekstur rumput menjadi kurang jelas. Ini membuktikan fungsi LPF sebagai pereduksi noise.Nilai Rata-rata: Nilainya hampir sama dengan citra asli. Hal ini karena kernel LPF yang digunakan memiliki jumlah total elemen sama dengan 1 ($9 \times 1/9 = 1$), sehingga energi atau tingkat kecerahan rata-rata gambar tetap terjaga.High Pass Filter (HPF):Visual: Citra didominasi warna hitam, namun garis-garis tepi objek (mata, hidung, dan garis luar surai) terlihat menonjol dengan warna putih/abu-abu terang.Nilai Rata-rata: Nilainya sangat kecil (mendekati 0). Secara matematis, jumlah seluruh elemen di dalam kernel HPF ini adalah $0$ ($-1 \times 8 + 8 = 0$). Karena area yang warnanya seragam akan menghasilkan nilai 0 setelah konvolusi, maka hanya area dengan perubahan intensitas tajam (tepi) yang tersisa.Band Pass Filter / Sharpening (BPF):Visual: Citra terlihat lebih tajam dan "pedas" dibanding aslinya. Detail kecil pada surai singa menjadi lebih kontras dan menonjol.Nilai Rata-rata: Nilainya cenderung stabil atau sedikit meningkat dibanding asli. Kernel ini bekerja dengan memperkuat perbedaan antara piksel pusat dengan tetangganya tanpa membuang informasi dasar gambar.2. Hubungan Domain Spasial dan Domain FrekuensiTerdapat korelasi langsung antara manipulasi piksel di Domain Spasial dengan karakteristiknya di Domain Frekuensi:Low Pass Filter: Di domain frekuensi, filter ini bertindak sebagai penghambat frekuensi tinggi (yang mewakili detail tajam dan noise) dan hanya meloloskan frekuensi rendah (warna latar belakang yang luas/homogen). Di domain spasial, ini dicapai dengan merata-ratakan nilai piksel.High Pass Filter: Filter ini memblokir frekuensi rendah (informasi kecerahan umum) dan hanya melewatkan frekuensi tinggi (perubahan mendadak). Hasilnya di domain spasial adalah hilangnya area luas yang warnanya sama, menyisakan hanya garis-garis tepi objek.Band Pass Filter (Sharpening): Filter penajaman bekerja dengan mengisolasi komponen frekuensi tinggi lalu menambahkannya kembali ke citra asli. Secara spasial, ini berarti kita memperkuat kontras lokal pada area yang memiliki perubahan warna mendadak agar terlihat lebih detail.
