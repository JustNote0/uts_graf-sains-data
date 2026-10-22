# 🕸️ Sistem Rekomendasi E-Commerce dengan Neo4j

**UTS Graf Sains Data** · S1 Sains Data · Universitas Negeri Surabaya

| | |
|---|---|
| **Nama** | Nurus Shobah Hidayati |
| **NIM** | 23031554163 |
| **Kelas** | Sains Data 2023-D |

---

## ✨ Tentang Proyek

Membangun sistem rekomendasi produk dari log perilaku pengunjung toko online ([RetailRocket](https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset)) menggunakan **graf Neo4j** dan **Python**.

Alurnya: data interaksi → graf → vektor (VSM) → proyeksi → similarity → rekomendasi KNN → evaluasi.

## 📅 Periode Data

| | Rentang (UTC) | Interaksi | Visitor |
|---|---|---|---|
| **P1** (training) | 1 – 20 Juni 2015 | 408.640 | 212.988 |
| **P2** (testing) | 21 – 30 Juni 2015 | 201.753 | 107.636 |

Visitor yang muncul di kedua periode: **6.792**.

## 🔎 Hasil Utama

**🧩 Komposisi graf (P1)**

| Simpul | Jumlah | Relasi | Jumlah |
|---|---|---|---|
| `Visitor` | 212.988 | `VIEWED` | 395.078 |
| `Item` | 94.576 | `ADDED_TO_CART` | 10.189 |
| | | `BOUGHT` | 3.373 |

**📐 VSM:** matriks user × item berukuran **212.988 × 94.576** dengan kepadatan **0,0016%** (sangat sparse). Bobot interaksi: view = 1, addtocart = 3, transaction = 5.

**⚖️ Proyeksi terbaik: Item-Item**

| Proyeksi | Simpul | Sisi (batas atas) | Sisi per simpul |
|---|---|---|---|
| User-User | 212.988 | 3.026.485 | 14,21 |
| **Item-Item** ✅ | **94.576** | **1.841.905** | **19,48** |

Lebih kecil, lebih padat, dan hubungan antar produk lebih stabil dibanding perilaku user.

**🔗 Similarity (cosine) pada item acuan `5411`**

| Item mirip | Skor |
|---|---|
| 33030 | 0,1949 |
| 33956 | 0,1054 |
| 358234 | 0,1027 |
| 375492 | 0,0805 |
| 89143 | 0,0756 |

Skor disimpan kembali ke Neo4j sebagai relasi `SIMILAR_TO`.

**🎯 Rekomendasi KNN (k = 5)**

- User terpilih: `1082219` (acak, `seed = 42`)
- 3 item yang diiklankan: **316114, 313064, 90618**
- Evaluasi: **Hit@5 = 0**, **NDCG@5 = 0**. User ini hanya menyentuh 1 item di P2, sehingga evaluasi satu user sangat sensitif.

## 🖼️ Graf Sebelum dan Sesudah Similarity

| Sebelum | Sesudah |
|---|---|
| <img src="https://github.com/user-attachments/assets/a9b30593-e3f9-4f71-b161-9f328f8896f8" alt="Graf sebelum similarity" width="100%"> | <img src="https://github.com/user-attachments/assets/b3f6664c-910c-4b96-9b5e-f4f2204969ff" alt="Graf sesudah similarity" width="100%"> |


## 🗂️ Isi Repositori

```
├── uts_graf_sains_data.ipynb   # notebook utama (kode + penjelasan)
├── requirements.txt            # daftar paket
├── data/
    ├── event.csv
│   ├── events_p1.csv           # data P1 hasil filter
│   └── events_p2.csv           # data P2 hasil filter
├── graf/
    ├── sebelum.png            # graf Neo4j sebelum 
    └── sesudah.png             # graf Neo4j sesudah
└── README.md
```

## ▶️ Cara Menjalankan

1. Install **Neo4j Desktop**, buat instance, lalu **Start** sampai berstatus *Running*.
2. Buat environment dan install paket:
   ```
   python -m venv myenv
   myenv\Scripts\activate
   pip install -r requirements.txt
   ```
3. Buka `uts_graf_sains_data.ipynb`, pilih kernel `myenv`, ganti password Neo4j pada sel koneksi, lalu jalankan semua sel.

---
