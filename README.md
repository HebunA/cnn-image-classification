# 🧠 CNN Modeli – Görüntü Sınıflandırma

---

## 📌 Proje Amacı

Bu proje, **Evrişimli Sinir Ağı (Convolutional Neural Network - CNN)** modeli kullanılarak görsellerin sınıflandırılmasını amaçlamaktadır. Eğitim süreci, doğrulama sonuçları ve test performansı detaylı olarak analiz edilmiştir.

## Veri Seti

Bu proje için kullanılan veri setine aşağıdaki bağlantıdan ulaşabilirsiniz:

[5-class weather status image classification - Kaggle](https://www.kaggle.com/datasets/ammaralfaifi/5class-weather-status-image-classification)


## 📂 Proje İçeriği & Model Detayları

### Veri Yükleme & Ön İşleme

* Görseller eğitim, doğrulama ve test klasörlerinden alınmıştır.
* Görseller **ImageDataGenerator** ile **0–1 aralığında normalize** edilmiştir.
* Giriş boyutu (`target_size`) **(64, 64)** olarak ayarlanmıştır.

### Model Mimarisi (Sequential CNN)

* `Conv2D` + `MaxPooling2D` katmanları (Özellik Çıkarma)
* `Flatten` katmanı (Vektörleştirme)
* `Dense` katmanları (Tam bağlı sinir ağı)
* `Dropout` (Overfitting'i önleme)
* Çıkış katmanında çoklu sınıflandırma için `softmax` aktivasyonu kullanılmıştır.

### Eğitim Parametreleri

* **Epochs:** 100
* **Batch Size:** 128
* **Loss:** `categorical_crossentropy`
* **Optimizer:** Adam (`learning_rate=0.0005`)
* **Metric:** `accuracy`

---

## 📊 Performans Değerlendirmesi

Modelin 100 epoch sonunda ulaştığı doğruluk (accuracy) oranları:

* **Eğitim Seti Doğruluğu:** %86
* **Doğrulama Seti Doğruluğu:** %85
* **Test Seti Doğruluğu:** %86

---

## 🔎 Model Açıklanabilirliği – Grad-CAM

Modelin tahmin sürecini daha anlaşılır hale getirmek için **Grad-CAM** yöntemi kullanılmıştır. Bu yöntem, modelin görselin hangi bölgelerine odaklandığını **ısı haritası (heatmap)** ile gösterir.

📸 Örnek:

![Modelin Neye Odaklandığını Gösteren Grad-CAM Görseli](gorseller/grad_cam_ornek.png)

Görüntüde **kırmızı bölgeler**, modelin sınıflandırma yaparken en çok dikkate aldığı alanları göstermektedir.

---

## ⚙️ Kullanım

1.  Gerekli bağımlılıkları yükleyin:

    ```bash
    pip install tensorflow numpy pandas matplotlib scikit-learn
    ```

2.  Verinizi `train/`, `val/`, `test/` klasörlerine sınıflara ayrılmış şekilde yerleştirin.

3.  Jupyter/Kaggle Notebook’u çalıştırın:
    * Eğitim için `model.fit()`
    * Değerlendirme için grafikler ve `model.evaluate()`
    * Tahmin için `model.predict()` örnekleri

---

## 🔮 İleri Çalışmalar

* **Veri Artırma (Data Augmentation)** (zoom, rotation, flip vb.) ile veri çeşitliliği artırılabilir.
* **Transfer Learning** (VGG16, ResNet50 gibi) kullanılarak daha yüksek başarı sağlanabilir.
* **Hiperparametre optimizasyonu** (learning rate, batch size) yapılabilir.

---

## 📜 Lisans

Bu proje eğitim amaçlı hazırlanmıştır. Kaggle notebook’unu referans alabilirsiniz:

👉 [CNN Modeli - Kaggle Notebook](https://www.kaggle.com/code/hebunartut/cnn-modeli)
