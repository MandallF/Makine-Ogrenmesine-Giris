# Oyun Veri Seti Üzerinde Gözetimli Öğrenme Analizi:  
Bu proje, oyunlara ait bir veri setinin ilk 10.000 satırı üzerinde gözetimli öğrenme yöntemlerini uygulayarak regresyon ve sınıflandırma modelleri ile performans karşılaştırması yapılmasını amaçlamaktadır.

Veri setinde çeşitli oyunlara ait satış verileri, meta skorlar, kullanıcı puanları ve farklı kategorik bilgileri içeren çok boyutlu bir yapı bulunmaktadır. Projenin temel amacı, bu çok boyutlu verinin uygun şekilde ön işlenerek makine öğrenmesi modellerine verilmesi ve modellerin başarılarının karşılaştırılmasıdır.

## Proje Yapısı
`Oyun Veri Setinin İncelenmesi.ipynb` Tüm veri analizini, model eğitimini ve görselleştirmeleri içeren Jupyter Notebook
`all_games.csv`  Çalışmada kullanılan oyun veri seti
`README.md`  Projenin açıklama dosyası

##  Amaç

1. Veri setindeki değişkenleri analiz etmek,  
2. Eksik değerleri ve uygun olmayan sütunları temizlemek,  
3. Sayısal ve kategorik değişkenlere uygun ön işleme adımları uygulamak,  
4. Hem regresyon hem sınıflandırma için hedef değişken belirlemek,  
5. Birden fazla makine öğrenmesi modeli eğiterek performanslarını karşılaştırmak,  
6. Sonuçları grafiklerle ve metriklerle değerlendirmek.

## Veri Ön İşleme

Proje kapsamında şu adımlar uygulanmıştır:

- İlk 10.000 satırı seçtim çünkü veriyi işlemek kullandığım sistemden ötürü çok uzun vakit alıyordu.
- Gereksiz sütunların kaldırılması (daha çok modeli yoracak, işlemesi zor string veriler) (`name`, `id`, `description` vb.).
- Uzun metin içeren sütunları ayıkladım.
- Seçtiğim sütunlardaki eksik değerleri doldurdum.
- Kategorik verilerin One-Hot Encoding yapılması
- Sayısal verilerin Standard Scaling yapılması
- Tüm işlemlerin bir Pipeline içinde yaptım. Bu sayede farklı modelleri eğitmek amacıyla bunu kullanabilirim.

### Kullanılan Modeller

### Regresyon Modelleri
- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor
- Support Vector Regressor (SVR)
- KNN Regressor

###  Sınıflandırma Modelleri
- Logistic Regression
- Decision Tree Classifier
- Random Forest Classifier
- Support Vector Machine (SVM)
- KNN Classifier
- Naive Bayes

##  Model Değerlendirme Metrikleri

###  Regresyon:
- **MSE** (Mean Squared Error), modelin hata oranı olarak düşünülebilir.
- **R² Score**, modelin doğruluk oranı olarak düşünülebilir

###  Sınıflandırma:
- Accuracy, modelin tüm tahminlerinin ne kadarının doğru olduğunu gösterir.
- Precision, modelin kesinlik değerini gösterir.
- Recall, bulduğu sonuç ne kadar doğru olduğunu gösterir. Sonuçların ne kadarı doğru buldu diye veya gözden kaçırdı mı anlamında düşünülebilir.
- F1-score, modelin bulduğu sonuç ne kadar kesin ve ne kadarını buldu, gözden kaçırdı mı metriğini tutan değer.  

##  Görselleştirmeler

Notebook içinde şu grafikler üretilmiştir:

- Hedef değişkenin histogram dağılımı
- Sınıflandırma modellerinin karşılaştırmalı doğruluk grafiği, modellerin karşılaştırılması.

Bu görseller modellerin performansını daha iyi anlamak için kullanılmıştır.


##  Sonuçlar

Analiz sonucunda:

### ✔️ En iyi regresyon modeli: Random Forest Regressor olarak bulundu
- En düşük MSE değerini yani hatayı üretmiştir  
- Yüksek R² yani doğruluk ile veri yapısını en iyi modelleyen algoritmadır  
- Karmaşık ve çok boyutlu veri üzerinde çok başarılıdır. Çünkü alt ağaçları birleştirerek çalışıyor. Bu sayede aşırı öğrenmeye de kaymıyor.  

### ✔️ En iyi sınıflandırma modeli: Random Forest Classifier
- En yüksek accuracy ve F1-score değerlerini elde etmiştir  
- Gürültülü ve karmaşık veri yapısını etkin biçimde işlemiştir  
- Diğer modellere göre daha stabil sonuçlar vermiştir, aşırı öğrenmeye kaymamıştır.  

Sonuç olarak, bu veri seti üzerinde hem regresyon hem sınıflandırma görevlerinde Random Forest tabanlı yöntemlerin en uygun yaklaşım olduğu belirlenmiştir.

---

##  Kullanılan Kütüphaneler

- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn
- warnings

---
Çalıştırma
Google Colab ile çalışmak isterseniz CSV dosyasını yüklemeniz yeterlidir.

Lisans
Bu proje eğitim amaçlı hazırlanmıştır. Her türlü kullanım serbesttir.

İletişim
Bursa Teknik Üniversitesi Bilgisayar Mühendisliği Bölümü 22360859047 numaralı 3. Sınıf Öğrencisi Kubilay İnanç
