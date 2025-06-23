### **FInal Project ML: Analisis Komparatif Model untuk Klasifikasi Genre Musik**

#### **Abstract**

Project ini melakukan **implementation** dan perbandingan empat **model architecture**, yaitu CNN, CRNN-GRU, CRNN-LSTM, dan SVM, untuk tugas **music genre classification** pada **dataset** GTZAN. Tujuan utamanya adalah melakukan **replication** terhadap **methodology** dari paper acuan dan menganalisis kinerjanya. Hasil **eksperimen** menunjukkan bahwa **model** yang lebih sederhana (CNN dan SVM) mengungguli **architecture** CRNN yang lebih kompleks, mengindikasikan pentingnya representasi **global feature** untuk **dataset** ini.

-----

#### **Methodology**

  * **Dataset:** **GTZAN Music Genre Dataset**, terdiri dari 1000 klip audio dari 10 genre musik.
  * **Feature Extraction:** **Feature** audio diekstrak menggunakan **MFCC (*Mel-Frequency Cepstral Coefficients*)** sebanyak 23 koefisien.
  * **Model Architecture yang Diuji:**
    1.  **CNN (Baseline):** Sebuah **model** konvolusional standar dengan `GlobalAveragePooling2D` sebagai *benchmark*.
    2.  **CRNN-GRU (Replication):** **Replication** dari **architecture** paper, menggunakan 3 blok CNN, lapisan `Reshape`, dan 2 lapisan `GRU` (20 *unit*).
    3.  **CRNN-LSTM (Replication):** **Replication** dari **architecture** paper, menggunakan 3 blok CNN, lapisan `Reshape`, dan 2 lapisan `LSTM` (30 *unit*).
    4.  **SVM (Classic):** **Model** *Support Vector Machine* yang dilatih menggunakan **feature** yang diekstrak dari CNN Baseline.

-----

#### **Results & Analysis**

**Tabel Perbandingan Performance**

```
                    Accuracy  F1-Score (Macro)
Model
SVM (CNN Features)     0.8000            0.7992
CNN (Baseline)         0.7900            0.7891
CRNN-LSTM              0.6850            0.6799
CRNN-GRU               0.6600            0.6627
```

![image](https://github.com/user-attachments/assets/f1ba605b-8a0e-4dc0-8034-76109b965a2d)


**Analysis Temuan:**

  * **Kinerja Berlawanan dengan Acuan:** Berbeda dengan **hypothesis** pada paper, **model** CNN dan SVM menunjukkan **performance** tertinggi. **Architecture** CRNN yang secara teoritis lebih kompleks justru menghasilkan **accuracy** yang lebih rendah.
  * **Hypothesis Penyebab:**
      * **Efektivitas Global Feature:** Keberhasilan **model** CNN/SVM mengindikasikan bahwa **global feature** (dari `GlobalAveragePooling2D`) lebih efektif untuk **dataset** GTZAN dibandingkan **sequential-temporal analysis** oleh RNN.
      * **Risiko *Overfitting***: **Model** CRNN yang lebih kompleks berpotensi mengalami ***overfitting*** pada **dataset** yang relatif terbatas ini, sehingga gagal melakukan generalisasi dengan baik.

-----

#### **Conclusion**

1.  **Implementation** dan **evaluation** keempat **model** telah berhasil dilakukan.
2.  Untuk kasus **dataset** GTZAN, **architecture** yang lebih sederhana (CNN dan SVM berbasis **CNN feature**) terbukti lebih *robust* dan akurat.
3.  Project ini menggarisbawahi bahwa kompleksitas **model** harus disesuaikan dengan karakteristik **dataset**; **model** yang lebih kompleks tidak selalu menjamin hasil yang lebih baik.

