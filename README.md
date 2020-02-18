# Tugas 01 - ETL menggunakan KNIME

Repo ini berisi jawaban tugas 1 kelas Big Data oleh Alifiannisa Alyahasna Wighneswara (05111740000011), yaitu implementasi ETL menggunakan KNIME

## Business Understanding
**World Happiness Report** merupakan hasil dari survei yang dilakukan untuk mengetahui kondisi kebahagiaan global. Laporan ini terus mendapatkan pengakuan global karena pemerintah, organisasi dan masyarakat sipil semakin menggunakan indikator kebahagiaan untuk menginformasikan keputusan pembuatan kebijakan mereka. Pakar terkemuka di berbagai bidang - ekonomi, psikologi, analisis survei, statistik nasional, kesehatan, kebijakan publik, dan lainnya - menggambarkan bagaimana pengukuran kesejahteraan dapat digunakan secara efektif untuk menilai kemajuan negara. Laporan tersebut meninjau keadaan kebahagiaan di dunia saat ini dan menunjukkan bagaimana ilmu kebahagiaan yang baru menjelaskan variasi kebahagiaan pribadi dan nasional.

Laporan ini terdiri dari 6 bagian, yaitu laporan kebahagiaan global tahun 2015, 2016, 2017, 2018, dan 2019. Untuk tugas ini digunakan laporan tahun **2019**.

Ada banyak hal yang bisa digali dari laporan ini, di antaranya:

 1. Parameter mana yang paling memengaruhi kebahagaan suatu negara?
 2. Apa yang membedakan satu negara dengan negara lainnya?
 3. Bagaimana tingkat kebahagiaan suatu negara dibandingkan negara lainnya?

## Data Understanding

Pada laporan tahun 2019, laporan terdiri dari **9 kolom** dan **156 baris**. Baris-baris dalam laporan berisi nama negara, peringkat kebahagiaan, skor total, dan nilai dari masing-masing parameter penilaian.

 1. **Overall rank** : peringkat kebahagiaan suatu negara
 2. **Country** : nama negara yang dinilai
 3. **Score** : total nilai dari semua parameter
 4. **GDP per capita** : besarnya pendapatan rata-rata penduduk suatu negara
 5. **Social support** : rata-rata nasional tanggapan biner (0 atau 1) dari pertanyaan “Jika Anda dalam masalah, apakah Anda memiliki kerabat atau teman yang dapat Anda andalkan untuk membantu Anda kapan pun Anda membutuhkannya, atau tidak?"
 6. **Healthy life expectancy** : angka harapan hidup sehat untuk menghitung jumlah tahun dimana bayi yang baru lahir dapat hidup dengan sehat.
 7. **Freedom to make life choices** : rata-rata nasional tanggapan biner (0 atau 1) dari pertanyaan “Apakah Anda merasa puas atau tidak puas atas kebebasan untuk memilih jalan hidup Anda?"
 8. **Generosity** : rata-rata nasional dari respons terhadap pertanyaan, “Sudahkah Anda menyumbangkan uang untuk amal dalam sebulan terakhir?” tentang PDB per kapita.
 9. **Perceptions of corruption** : rata-rata jawaban biner untuk dua pertanyaan: "Apakah korupsi tersebar luas di seluruh pemerintah atau tidak?" dan "Apakah korupsi tersebar luas dalam bisnis atau tidak?".

## Data Preparation

Pada data preparation, digunakan node **Column Splitter** untuk memisahkan data menjadi dua bagian. Bagian pertama berisi kolom Overall rank, GDP per capita, Social support, Healthy life expectancy, Freedom to make choices, Generosity, dan Perceptions of corruption. Bagian kedua berisi kolom Country dan Score.

***Isi gambar SC 2 kolom disini***

Setelah itu, kolom pertama disimpan dalam database dan kolom kedua disimpan sebagai file CSV.

Untuk menyimpan kolom pertama, database di localhost harus disambungkan terlebih dahulu dengan KNIME menggunakan node **MySQL Connector**. Konfigurasi penyambungan database adalah sebagai berikut.

***Isi konfigurasi penyambungan database disini***

Setelah disambungkan ke database, partisi bagian pertama akan disimpan ke dalam database menggunakan node **DB Writer**. Adapun konfigurasinya adalah sebagai berikut.

***Isi konfigurasi DB Writer disini***

Setelah DB Writer dijalankan, di skema akan terbentuk satu tabel baru bernama scores yang merupakan tabel dari data pertama.

***Isi sc database disini***

Partisi bagian kedua akan disimpan ke dalam file CSV. Untuk menyimpan tabel ke dalam sebuah file CSV, dibutuhkan node **CSV Writer**. Adapun konfigurasinya adalah sebagai berikut.

***Isi konfigurasi CSV Writer disini***

Setelah node dijalankan, file CSV baru akan terbuat dan akan terlihat seperti ini.

***Isi sc csv disini***


