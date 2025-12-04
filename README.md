# Oyun Veri Seti Üzerinde Gözetimli Öğrenme Analizi:  
Bu proje, oyunlara ait bir veri setinin ilk 10.000 satırı üzerinde gözetimli öğrenme yöntemlerini uygulayarak regresyon ve sınıflandırma modelleri ile performans karşılaştırması yapılmasını amaçlamaktadır.

Veri setinde çeşitli oyunlara ait satış verileri, meta skorlar, kullanıcı puanları ve farklı kategorik bilgileri içeren çok boyutlu bir yapı bulunmaktadır. Projenin temel amacı, bu çok boyutlu verinin uygun şekilde ön işlenerek makine öğrenmesi modellerine verilmesi ve modellerin başarılarının karşılaştırılmasıdır.

## Proje Yapısı
Oyun Veri Setinin İncelenmesi.ipynb, Tüm veri analizini, model eğitimini ve görselleştirmeleri içeren Jupyter Notebook

all_games.csv,  Çalışmada kullanılan oyun veri seti

README.md,  Projenin açıklama dosyası

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
- Linear Regression, Veri ile hedef arasında doğrusal (lineer) bir ilişki kurarak tahmin yapan basit regresyon modelidir.
- Decision Tree Regressor, Karar kurallarına dayalı dallanma yapısı oluşturarak hedef değeri tahmin eden ağaç tabanlı regresyon modelidir.
- Random Forest Regressor, Birden fazla karar ağacının ortalama tahminini kullanarak daha istikrarlı ve güçlü sonuç üreten topluluk regresyon yöntemidir.
- Support Vector Regressor (SVR), Verileri belirli bir tolerans aralığında en iyi şekilde ayıran hiper düzlemi bulup tahmin yapan margin-tabanlı regresyon modelidir.
- KNN Regressor, Hedef değeri, en yakın komşu verilerin ortalamasına bakarak hesaplayan örnek-tabanlı regresyon yöntemidir.

###  Sınıflandırma Modelleri
- Logistic Regression, Verinin belirli bir sınıfa ait olma olasılığını hesaplayan istatistiksel sınıflandırma modelidir.
- Decision Tree Classifier, Veriyi “evet/hayır” sorularıyla dallara ayırarak sınıf etiketi tahmini yapan ağaç tabanlı modeldir.
- Random Forest Classifier, Birçok karar ağacının oylamasıyla daha kararlı sınıf tahmini yapan topluluk sınıflandırma yöntemidir.
- Support Vector Machine (SVM), Sınıfları en iyi ayıran sınır (hiper düzlem) oluşturarak maksimum ayrım sağlayan sınıflandırma algoritmasıdır.
- KNN Classifier, Bir örneğin sınıfını, en yakın komşularının çoğunluğuna bakarak belirleyen basit ve etkili sınıflandırma yöntemidir.
- Naive Bayes, Özelliklerin birbirinden bağımsız olduğunu varsayarak olasılık temelli sınıf tahmini yapan hızlı ve hafif modeldir.

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

- pandas, genel olarak veriyi işleme aşamasında kullanıldı.
- numpy, genel olarak veriyi işleme aşamasında kullanıldı.
- scikit-learn, veriyi train ve test verisi olarak ayırıp modeli eğitmek amacıyla kullanıldı.
- matplotlib, grafikleri çizmek amacıyla yararlanıldı.

- <img width="491" height="752" alt="image" src="https://github.com/user-attachments/assets/078b29d9-7d06-4b62-92de-a7b8be247ab4" />

Detaylı grafik bilgileri proje kısmında belirtilmiştir.


---
Çalıştırma
Google Colab ile çalışmak isterseniz CSV dosyasını yüklemeniz yeterlidir.

Lisans
Bu proje eğitim amaçlı hazırlanmıştır. Her türlü kullanım serbesttir.

İletişim
Bursa Teknik Üniversitesi Bilgisayar Mühendisliği Bölümü 22360859047 numaralı 3. Sınıf Öğrencisi Kubilay İnanç
