# Jawaban UTS (mungkin) - Simulasi dan Pemodelan

## Simulasi

Simulasi diartikan sebagai suatu kegiatan menirukan suatu hal (seperti proses, fasilitas, obyek dll) pada dunia nyata yang nantinya akan menghasilkan suatu model nyata. Kemudian dilakukan eksperimen terhadap model tersebut dengan tujuan untuk memahami perilaku suatu hal tersebut agar nantinya hasil eksperimen yang sesuai diterapkan pada dunia nyata.

## Sistem

Sistem adalah suatu kumpulan dari entitas (seperti orang, mesin, obyek tertentu dll) yang saling berhubungan satu sama lain dan bersama-sama bertugas untuk mencapai suatu tujuan tertentu seperti menghasilkan suatu produk atau jasa.

## Model

Model adalah representasi dari suatu obyek pada dunia nyata dengan menekankan berbagai karakteristik penting yang dimiliki oleh obyek tersebut dan mengabaikan aspek-aspk yang tidak relevan.

Model dapat dibedakan menjadi dua macam, yakni model fisik dan model matematika.

## Simulasi _Monte Carlo_

Simulasi _Monte Carlo_ adalah suatu teknik simulasi yang digunakan jika sebuah sistem yang akan dilakukan simulasi mengandung unsur yang menunjukan adanya peluang dalam perilakunya.

5 langkah dalam melakukan simulasi _monte carlo_ yakni :

1. Menentukan distribusi probabilitas.
2. Membuat distribusi probabilitas kumulatif.
3. Menentukan interval bilangan acak.
4. Membangkitkan bilangan acak (_generate random number_).
5. Melakukan serangkaian simulasi percobaan.

Contoh penerapan simulasi _monte carlo_ yakni untuk memprediksi penjualan suatu barang.

## Simulasi Kontinyu

Simulasi Kontinyu adalah suatu jenis simulasi yang mana status atau keadaan sistem pada simulasi ini direpresentasikan oleh variabel dependen (terikat) yang berubah sepanjang waktu.

Contoh penerapan simulasi kontinyu :

-   Simulasi pembangunan tanggul bendungan dan konstruksi terowongan.
-   Pada bidang militer digunakan untuk mensimulasikan lintasan rudal.
-   Analisis arus penumpang di terminal bandara.

## Simulasi Diskrit

**Simulasi diskrit** adalah suatu jenis simulasi yang mana perubahan statusnya terjadi pada titik-titik terpisah (diskrit) dalam waktu yang dipicu oleh kejadian (_event_). Kejadian ini biasanya adalah kedatangan (_arrival_) atau kepulangan (_departure_) suatu entitas pada suatu sistem.

Contoh penerapan simulasi diskrit :

-   Antrian seperti pada bank, minimarket ataupun rumah sakit.
-   Penyimpanan barang pada gudang yang mana barang datang dan masuk pada waktu tertentu.

## Perbedaan Simulasi Diskrit dan Simulasi Kontinyu

Perbedaan utama dari simulasi diskrit dan simulasi kontinyu adalah terkait tentang **perubahan status atau kondisi pada suatu sistem yang dilakukan simulasi**. Pada simulasi diskrit status sistem dapat berubah sewaktu-waktu, sedangkan pada simulasi kontinyu status sistem berubah sepanjang waktu.

Pada segi _pemerolehan data_ pada **simulasi diskrit** dilakukan dengan **pencacahan atau perhitungan** sedangkan pada **simulasi kontinyu** dilakukan **pengukuran**.

Sifat nilai dari **simulasi diskrit** adalah **spesifik/terpisah** sedangkan pada **simulasi kontinyu** **berada dalam interval**.
