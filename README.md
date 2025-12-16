# 🧠 CNN Tabanlı Görüntü Sınıflandırma Projesi  
**Model Karşılaştırması: Transfer Learning ve Özel CNN Mimarileri**

Bu projede, kullanıcı tarafından oluşturulmuş bir görüntü veri seti üzerinde
Convolutional Neural Network (CNN) tabanlı sınıflandırma modelleri geliştirilmiş
ve performansları karşılaştırılmıştır.

Çalışma kapsamında hem **state-of-the-art transfer learning mimarileri**
hem de **sıfırdan eğitilen CNN modelleri** kullanılarak,
hiperparametrelerin ve veri artırımı tekniklerinin model başarısına etkisi
analiz edilmiştir.

---

## 📁 Veri Seti

- Veri seti **tamamen kullanıcı tarafından oluşturulmuştur**.
- İnternetten indirilen veya hazır veri setleri kullanılmamıştır.
- Görüntüler telefon kamerası ile çekilmiş olup,
  farklı açı, ışık koşulu ve arka plan çeşitliliği sağlanmıştır.

### Sınıflar
- **Şişe**
- **Kutu**

### Klasör Yapısı
dataset_split/
├── train/
│ ├── sise/
│ └── kutu/
├── val/
│ ├── sise/
│ └── kutu/
└── test/
├── sise/
└── kutu/


Tüm görüntüler eğitim öncesinde **128x128 piksel** boyutuna yeniden ölçeklendirilmiştir.

---

## 🧪 Model 1 – Transfer Learning (State-of-the-Art)

Bu aşamada, ImageNet veri seti üzerinde önceden eğitilmiş
state-of-the-art CNN mimarileri kullanılmıştır.
Amaç, önceden öğrenilmiş görsel özelliklerin
küçük ve özel bir veri seti üzerindeki etkisini incelemektir.

Kullanılan mimariler:
- **VGG16**
- **ResNet50**
- **MobileNetV2**

Ortak özellikler:
- ImageNet ağırlıkları kullanılmıştır.
- Temel ağlar dondurulmuş (`trainable = False`) ve sadece üst katmanlar eğitilmiştir.
- Çıkış katmanı iki sınıflı problem için sigmoid aktivasyon fonksiyonu ile oluşturulmuştur.

Notebook dosyaları:
- `Model1_VGG16.ipynb`
- `Model1_ResNet50.ipynb`
- `Model1_MobileNetV2.ipynb`

---

## 🧪 Model 2 – Basit CNN (Sıfırdan Eğitim)

Bu aşamada, CIFAR-10 örneğine benzer şekilde
sıfırdan tanımlanmış basit bir CNN mimarisi kullanılmıştır.

Model özellikleri:
- 2 adet Conv2D + MaxPooling katmanı
- Flatten ve Dense katmanlar
- Dropout ile aşırı öğrenme kontrolü
- Öğrenme oranı manuel olarak ayarlanmıştır

Bu model, transfer learning kullanılmadan
CNN’in temel öğrenme kapasitesini gözlemlemek amacıyla geliştirilmiştir.

Notebook dosyası:
- `Model2.ipynb`

---

## 🧪 Model 3 – Geliştirilmiş CNN (Deneysel)

Model 3, Model 2 temel alınarak geliştirilmiş ve
performansı artırmak amacıyla çeşitli deneyler gerçekleştirilmiştir.

Yapılan geliştirmeler:
- Conv katman sayısının artırılması
- Filtre sayılarının değiştirilmesi
- Dropout oranlarının ayarlanması
- Öğrenme oranının düşürülmesi
- **Online veri artırımı (data augmentation)** uygulanması
- EarlyStopping kullanımı

Model 3’te, hiperparametreler tek bir yapı üzerinden
kontrollü şekilde değiştirilerek **birden fazla deney** yapılmıştır.
Elde edilen sonuçlar tablo halinde karşılaştırılmıştır.

Notebook dosyası:
- `Model3.ipynb`

---

## 📊 Deneyler ve Sonuçlar

Model 3 kapsamında yapılan deneylerde aşağıdaki parametreler incelenmiştir:
- Batch size
- Filtre sayısı
- Dropout oranı
- Öğrenme oranı
- Veri artırımı kullanımı

Deney sonuçları göstermektedir ki:
- Veri artırımı, modelin genelleme performansını artırmıştır.
- Filtre sayısının artırılması belirli bir seviyeye kadar fayda sağlamıştır.
- Aşırı dropout ve çok düşük öğrenme oranı bazı deneylerde performans düşüşüne yol açmıştır.

Genel olarak Model 3,
Model 2’ye kıyasla daha dengeli ve genellenebilir sonuçlar üretmiştir.

---

## 📈 Değerlendirme Kriterleri

Her model için aşağıdaki çıktılar raporlanmıştır:
- Eğitim doğruluk ve kayıp grafikleri
- Doğrulama doğruluk ve kayıp grafikleri
- Test seti doğruluğu ve kaybı
- Deney sonuçlarının karşılaştırmalı tablosu

---

## 🛠 Kullanılan Teknolojiler

- Python
- TensorFlow / Keras
- Google Colab
- NumPy
- Matplotlib
- Git & GitHub

---

## 🎯 Sonuç

Bu proje kapsamında:
- Transfer learning modellerinin küçük veri setlerinde avantajları,
- Basit CNN mimarilerinin sınırlamaları,
- Hiperparametre optimizasyonu ve veri artırımının önemi

uygulamalı olarak gösterilmiştir.

Model 3, yapılan iyileştirmeler sayesinde
Model 2’ye göre daha başarılı ve dengeli bir performans sergilemiştir.

Bu çalışma, CNN tabanlı görüntü sınıflandırma konularında
eğitsel ve deneysel amaçlarla hazırlanmıştır.
