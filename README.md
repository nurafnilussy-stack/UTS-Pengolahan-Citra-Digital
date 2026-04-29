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
