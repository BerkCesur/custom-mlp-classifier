# Türkiye Geneli Konut Fiyatı Sınıflandırması – Sıfırdan NumPy MLP

Bu proje, derin öğrenme modellerinin "kara kutu" (black box) doğasını kırmak ve yapay sinir ağlarının temelindeki matematiksel mimariyi tam anlamıyla kavramak amacıyla geliştirilmiştir. 

Projede TensorFlow, Keras veya PyTorch gibi hiçbir yüksek seviyeli derin öğrenme kütüphanesi kullanılmamış; İleri Yayılım (Forward Propagation), Geri Yayılım (Backpropagation) ve ağırlık optimizasyonu süreçleri yalnızca doğrusal cebir operasyonlarıyla (NumPy) sıfırdan tasarlanmıştır.

---

## Proje Mimarisi ve Teknik Yaklaşımlar

### 1. Matematiksel Altyapı ve Özelleştirilmiş Mimari
* **Manuel Geri Yayılım (Backpropagation):** Zincir kuralı (chain rule) ve gradyan inişi (gradient descent) algoritmaları, türev hesaplamalarıyla birlikte sıfırdan kodlanmıştır. Model, hata payını minimize etmek için ağırlık (weight) ve sapma (bias) güncellemelerini otonom olarak yapmaktadır.
* **Aktivasyon Fonksiyonları A/B Testi:** Modelin doğrusal olmayan (non-linear) problemleri çözme yeteneğini maksimize etmek için gizli katmanlarda ReLU ve Sigmoid aktivasyon fonksiyonları üzerine karşılaştırmalı A/B testleri uygulanmış; gradyan kaybolması (vanishing gradient) problemleri analiz edilmiştir.

### 2. Veri Seti ve Problem Tanımı
* **Amaç:** Türkiye genelindeki konutlara ait metrekare, oda sayısı, konum gibi bağımsız değişkenleri kullanarak, konutların fiyat segmentlerini (düşük, orta, yüksek) sınıflandırmak.
* **Veri Ön İşleme:** Modelin stabil eğitilebilmesi için veri seti üzerinde normalizasyon ve aykırı değer (outlier) temizliği işlemleri gerçekleştirilmiştir.

---

## Deneysel Sonuçlar ve Başarım Metrikleri

Geliştirilen özelleştirilmiş MLP modelinin performansı, makine öğrenmesi alanında endüstri standardı olarak kabul edilen Scikit-learn kütüphanesinin hazır MLPClassifier modeliyle karşılaştırılarak test edilmiştir.

* **Sıfırdan Yazılan Custom MLP Skoru:** %68.7 F1 Score
* **Sklearn MLPClassifier Skoru:** Modelimiz, endüstri standardı olan bu hazır kütüphane fonksiyonunu geride bırakarak daha yüksek bir başarım sergilemiştir.
* **Değerlendirme:** Bu sonuç, yalnızca yüksek seviyeli kütüphanelerin kullanıcısı olmak yerine, hiperparametreleri ve optimizasyon algoritmalarını temelden inşa etmenin modele ne kadar yüksek bir adaptasyon sağladığını kanıtlamaktadır.

---

## Kullanılan Teknolojiler
* **Programlama Dili:** Python
* **Temel Kütüphane:** NumPy (Matris operasyonları ve kalkülüs hesaplamaları için)
* **Kıyaslama ve Metrik Analizi:** Scikit-learn
* **Makine Öğrenmesi Yaklaşımı:** Multi-Layer Perceptron (MLP) Sınıflandırma

---

## Kurulum ve Çalıştırma

Projeyi yerel ortamınızda doğrulamak ve kodun temel yapısını incelemek için aşağıdaki adımları uygulayabilirsiniz:

1. Depoyu klonlayın:
```bash
git clone [https://github.com/berkburhancesur/numpy-mlp-from-scratch.git](https://github.com/berkburhancesur/numpy-mlp-from-scratch.git)
cd numpy-mlp-from-scratch
```

2. Gerekli kütüphaneleri yükleyin (sadece temel veri analizi kütüphaneleri gereklidir):
```bash
pip install numpy pandas scikit-learn
```

3. Modeli çalıştırın:
```bash
python mlp_model.py
```
