# 🛍️ RetailRocket Recommendation System

**UTS Graf Sains Data | S1 Sains Data — Universitas Negeri Surabaya**

Repository ini berisi dokumentasi pengerjaan Ujian Tengah Semester (UTS) mata kuliah Graf Sains Data pada Program Studi S1 Sains Data, Universitas Negeri Surabaya, Tahun Akademik 2026/2027.
Proyek ini berfokus pada pengolahan data interaksi pengguna dengan produk (e-commerce interaction data), pemodelan graf menggunakan Neo4j, analisis Vector Space Modelling (VSM), perhitungan similarity, serta penerapan algoritma K-Nearest Neighbors (KNN) untuk menghasilkan rekomendasi produk.

## 🎯 Objectives

- Data wrangling and exploratory data analysis (EDA).
- Graph modeling using Neo4j and Cypher.
- User-based and item-based Vector Space Modelling (VSM).
- Similarity analysis and graph visualization.
- Product recommendation using KNN (`k = 5`).
- Recommendation evaluation using Hit@5 and NDCG@5.

## 📂 Dataset

**RetailRocket E-commerce Dataset**

Dataset ini berisi interaksi pengguna terhadap produk, meliputi:

| Feature | Description |
|---|---|
| `visitorid` | Unique visitor ID |
| `itemid` | Unique product ID |
| `timestamp` | Interaction time |
| `event` | View, add to cart, or transaction |
| `transactionid` | Transaction ID |

🔗 [Dataset source — Kaggle](https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset)

## 🗓️ Periode Waktu Analisis

Analisis menggunakan dua periode waktu untuk memisahkan data training dan testing.

Periode 1 (Training): [01 Junil – 20 Juni]

Periode 2 (Testing): [21 Jnil – 30 Juni]

Pemfilteran dilakukan berdasarkan atribut timestamp. Hasil pemfilteran disimpan dalam file CSV untuk digunakan pada tahap analisis selanjutnya.

## 🛠️ Tools & Technologies

`Python` · `Pandas` · `Neo4j` · `Cypher` · `NetworkX` · `Matplotlib` · `Scikit-learn`

## 🔍 Workflow

1. **Data Preparation** — Filtering interactions into training and testing periods.
2. **Graph Construction** — Modeling visitors, items, and their interactions in Neo4j.
3. **Graph Analysis** — Exploring graph structure and comparing user-based and item-based projections using VSM.
4. **Similarity Analysis** — Calculating similarity and identifying the top five results.
5. **Recommendation** — Generating three product recommendations using KNN.
6. **Evaluation** — Measuring recommendation performance using Hit@5 and NDCG@5.

## 📓 Project Files

- `notebook/` — Jupyter Notebook containing code, explanations, and analysis results.
- `data/` — Dataset and filtered CSV files.
- `requirements.txt` — Python dependencies.

*Folder and file names may vary depending on the final repository structure.*

## 📊 Results

The analysis covers graph composition, projection characteristics, similarity scores, recommended products, and recommendation evaluation.

*Detailed results and visualizations are available in the notebook.*

---

**Course:** Graf Sains Data  
**Program:** S1 Sains Data, Universitas Negeri Surabaya  
**Academic Year:** 2026/2027
