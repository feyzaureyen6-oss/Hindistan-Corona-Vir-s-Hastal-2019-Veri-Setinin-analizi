# Hindistan COVID-19 Veri Seti Analizi

Bu proje, Hindistan COVID-19 vaka verileri üzerinde veri ön işleme, analiz ve sınıflandırma algoritmalarının karşılaştırmalı performanslarını incelemektedir. Amaç, bir günün yüksek vaka günü (1) mü yoksa düşük vaka günü (0) mü olacağını tahmin etmektir.

## Kullanılan Teknolojiler

- Python
- JupyterLab
- Kütüphaneler: pandas, numpy, matplotlib, scikit-learn

## Veri Seti

- Kaynak: Kaggle Hindistan COVID-19 verileri
- Boyut: 14.402 satır, 9 sütun

**Önemli sütunlar:**
- `Date` → Tarih
- `State/UnionTerritory` → Bölge bilgisi
- `Confirmed`, `Cured`, `Deaths` → Günlük vaka, iyileşen ve ölüm sayıları
- `daily_confirmed` → Günlük yeni vaka (hesaplanan özellik)
- `high_case_day` → Hedef değişken (0: düşük vaka, 1: yüksek vaka)

## Veri Ön İşleme Adımları

- Tarih formatı dönüştürüldü
- Eksik ve hatalı değerler temizlendi
- Günlük vaka sayısı (`daily_confirmed`) türetildi
- Negatif değerler sıfırlandı
- Özellikler standartlaştırıldı (`StandardScaler`)
- 1000 vaka eşiği üzerinden sınıflandırma etiketi (`high_case_day`) oluşturuldu

##  Kullanılan Modeller ve Sonuçlar

- **Logistic Regression** → %80 doğruluk (yüksek vaka günlerinde düşük performans)
- **k-NN (k=5)** → %92.9 doğruluk, yüksek vaka sınıfında başarılı
- **Decision Tree** → %96.2 doğruluk, her iki sınıfta da dengeli ve güçlü
- **Random Forest** → %96.2 doğruluk, aşırı öğrenmeye daha dayanıklı
- **SVM** → %91 doğruluk, yüksek vaka günlerinde görece zayıf
- **Naive Bayes** → %29 doğruluk, bu problem için uygun değil

 En iyi performansı Decision Tree ve Random Forest modelleri göstermiştir.

## Görselleştirmeler

- Karar ağacı diyagramı
- Karışıklık matrisleri (confusion matrix)
- Model performans metrikleri (precision, recall, f1-score)

##  Sonuç

- Decision Tree ve Random Forest, en güvenilir modeller olarak öne çıkmıştır.
- k-NN dengeli ve başarılı bir model olarak değerlidir.
- SVM bazı ayarlamalarla iyileştirilebilir.
- Logistic Regression ve Naive Bayes, yüksek vaka tahminlerinde yetersiz kalmıştır.
