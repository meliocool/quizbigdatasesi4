# 🚀 PREPARATION QUIZ SESSION 4 BIG DATA PROCESSING

## 📂 1. Pindahkan File `.csv` dan `.sql` ke Cloudera Desktop

Pindahkan file dari **Desktop Windows** ke **Desktop Cloudera** dengan **drag and drop**.

---

## 🖥️ 2. Buka Terminal dan Cek File

```bash
cd Desktop   # Pindah ke folder Desktop
ls           # Lihat isi file di Desktop
```

---

## 📤 3. Pindahkan File ke HDFS

Gunakan command `hadoop fs -copyFromLocal` untuk memindahkan file ke HDFS. Contoh untuk file `MsStore.csv`:

```bash
hadoop fs -copyFromLocal MsStore.csv /user/cloudera
```

---

## 🎛️ 4. Buat Database di Hue

Buka **Hue**, lalu buat database dengan command berikut:

```sql
CREATE DATABASE mydata;
```

Jika database belum muncul, lakukan **refresh** dengan memilih opsi **Invalidate all metadata and rebuild index**.

---

## 🏗️ 5. Buat Tabel untuk CSV

Ada dua tipe tabel:

- **Internal Table** 🏠 → Hanya digunakan di dalam sistem
- **External Table** 🌍 → Bisa digunakan di luar sistem

Contoh pembuatan **External Table**:

```sql
CREATE EXTERNAL TABLE msdrugtype(
   drugtypeid INT,
   drugtypename VARCHAR(255)
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE
TBLPROPERTIES ("skip.header.line.count"="1");
```

Lakukan eksekusi untuk semua tabel yang diperlukan.

📌 **Tip:** Gunakan `CTRL + SPACE` untuk autocomplete query di Hue!

---

## 🔒 6. Modifikasi Hak Akses File

Hak akses:

- **Read** 🧐 → `4`
- **Write** ✍ → `2`
- **Execute** 🚀 → `1`

Jika ingin memberikan akses penuh (`7 = 4+2+1`), jalankan command ini:

```bash
hadoop fs -chmod -R 777 /user/cloudera
```

---

## 📥 7. Load Data CSV ke Tabel di Hue

Gunakan command berikut untuk memasukkan data dari **HDFS** ke tabel **Hue**:

```sql
LOAD DATA INPATH '/user/cloudera/MsStore.csv' INTO TABLE msstore;
```

Lakukan langkah ini untuk semua tabel yang diperlukan.

---

## 🧐 8. Check Apakah Data sudah masuk ke Tabel

Gunakan command seperti ini

```sql
SELECT * FROM msstore;
```


