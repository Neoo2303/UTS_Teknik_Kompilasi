# Jawaban Pertanyaan Refleksi

## 1. Mengapa fungsi `power()` harus dipanggil di dalam `term()`, bukan sebaliknya? Jelaskan kaitannya dengan Operator Precedence.

Fungsi `power()` harus dipanggil di dalam `term()` karena operator pangkat (`^`) memiliki prioritas (*operator precedence*) lebih tinggi dibandingkan operator perkalian (`*`) dan pembagian (`/`).

Dalam proses parsing, urutan pemanggilan fungsi menentukan prioritas operasi matematika. Dengan memanggil `power()` di dalam `term()`, maka ekspresi pangkat akan diproses terlebih dahulu sebelum operasi perkalian atau pembagian dilakukan.

Contoh:
```python
a ^ 2 * b
```

Akan diproses menjadi:
```python
(a ^ 2) * b
```

Jika `term()` dipanggil terlebih dahulu sebelum `power()`, maka prioritas operator menjadi salah dan hasil parsing tidak sesuai aturan matematika.

---

## 2. Apa yang terjadi pada fase Analisis Semantik jika variabel `z` digunakan dalam kode sumber tetapi tidak ada di `symbol_table`?

Pada fase Analisis Semantik, compiler akan memeriksa apakah setiap variabel yang digunakan sudah dideklarasikan atau tersedia di dalam `symbol_table`.

Jika variabel `z` digunakan tetapi tidak ada di `symbol_table`, maka compiler akan menghasilkan *semantic error* karena variabel dianggap belum dikenali atau belum didefinisikan.

Contoh error:
```python
Semantic Error: Undefined variable 'z'
```

Hal ini penting untuk mencegah program menggunakan variabel yang tidak memiliki nilai atau identitas yang valid.

---

## 3. Jelaskan mengapa dalam TAC, instruksi untuk `a ^ 2` harus muncul sebelum instruksi untuk `+`.

Dalam Three Address Code (TAC), urutan instruksi mengikuti prioritas operasi matematika.

Karena operator pangkat (`^`) memiliki prioritas lebih tinggi daripada operator penjumlahan (`+`), maka operasi `a ^ 2` harus dihitung terlebih dahulu dan hasilnya disimpan ke variabel sementara sebelum digunakan dalam operasi penjumlahan.

Contoh:
```python
a ^ 2 + b
```

TAC yang benar:
```python
t1 = a ^ 2
t2 = t1 + b
```

Instruksi `a ^ 2` harus muncul lebih dulu agar nilai hasil pangkat sudah tersedia ketika operasi penjumlahan dilakukan. Jika urutannya dibalik, maka hasil perhitungan menjadi tidak sesuai dengan aturan operator precedence.
