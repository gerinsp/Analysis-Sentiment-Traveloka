# **Analisis Sentimen Aplikasi Traveloka**

Proyek ini bertujuan untuk melakukan **analisis sentimen terhadap aplikasi Traveloka di Google Play Store** menggunakan model **Long Short-Term Memory (LSTM)**. Analisis ini difokuskan pada ulasan berbahasa Indonesia yang diperoleh melalui proses scraping dari Google Play Store.

## **Deskripsi Proyek**
Dataset yang digunakan berisi **158.173 baris** data ulasan yang telah dikumpulkan dan dibagi menjadi dua bagian: **80%** untuk pelatihan dan **20%** untuk pengujian. Ulasan-ulasan ini dikelompokkan ke dalam tiga kelas sentimen: **positif**, **negatif**, dan **netral**.

### **Kinerja Model**
Setelah pelatihan, model menunjukkan hasil yang memuaskan dengan metrik sebagai berikut:
- **Akurasi Pelatihan**: 95.12%
- **Akurasi Pengujian**: 94.04%

### **Struktur Model**
Model LSTM yang digunakan dalam proyek ini memiliki arsitektur sebagai berikut:

```python
model = Sequential([
    Embedding(input_dim=vocab_size, output_dim=embedding_dim, weights=[embedding_matrix], input_length=max_length, trainable=False),
    Bidirectional(LSTM(64, return_sequences=True)),
    Dropout(0.5),
    Bidirectional(LSTM(32)),
    Dropout(0.5),
    Dense(32, activation='relu'),
    Dropout(0.5),
    Dense(3, activation='softmax')
])
```
### **Kinerja Model**
Model dilatih dengan parameter yang sudah diatur sebelumnya. Berikut adalah hasil yang dicatat selama proses pelatihan:
```aiignore
3955/3955 ━━━━━━━━━━━━━━━━━━━━ 47s 12ms/step - accuracy: 0.9515 - loss: 0.1367
```
Proses pengujian menghasilkan:

```aiignore
989/989 ━━━━━━━━━━━━━━━━━━━━ 12s 12ms/step - accuracy: 0.9404 - loss: 0.1733
```

### **Kesimpulan**
Proyek ini berhasil mengembangkan model LSTM yang efektif untuk analisis sentimen pada ulasan aplikasi Traveloka, dengan akurasi yang tinggi baik pada data pelatihan maupun pengujian. Model ini dapat digunakan untuk memahami persepsi pengguna terhadap aplikasi, yang dapat membantu pengembang dalam perbaikan dan pengembangan fitur baru.