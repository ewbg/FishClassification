# FishClassification

Kaggle: https://www.kaggle.com/code/bakwein/fishh

## Veri Kümesi

Veri kümesi, Kaggle'dan [Fish Dataset](https://www.kaggle.com/datasets) başlığı altından alınmıştır. Birçok balık türüne ait görüntüler içerir. Veri kümesi, her bir balık türü için bir klasör olacak şekilde düzenlenmiştir. Görüntüler `.png` formatında sağlanmıştır ve veri kümesinde 9 farklı balık türü bulunmaktadır.

## Teknolojiler ve Kütüphaneler

Bu projede kullanılan başlıca kütüphaneler ve teknolojiler şunlardır:

- **Python**: Proje için kullanılan ana programlama dili.
- **TensorFlow/Keras**: Derin öğrenme modellerini oluşturmak ve eğitmek için kullanıldı.
- **Pandas**: Veri kümesi işlemleri ve DataFrame oluşturmak için kullanıldı.
- **NumPy**: Sayısal işlemler ve dizilerle çalışmak için kullanıldı.
- **Matplotlib & Seaborn**: Veri görselleştirme ve grafik çizimleri için kullanıldı.
- **Scikit-learn**: Veri kümesini bölmek, etiketleri encode etmek ve karışıklık matrisi oluşturmak için kullanıldı.
- **ImageDataGenerator**: Veri artırma ve görüntü ön işleme için kullanıldı.

## Yapılan İşlemler

### 1. Veri Yükleme ve Ön İşleme

Veri kümesi, belirtilen dizinden yüklenir ve görüntü yolları ile etiketler çıkartılır. Yalnızca `.png` formatındaki görüntüler alınır ve gereksiz dosyalar (örneğin, GT klasörleri) filtrelenir.

### 2. Veri Artırma

Veri artırma teknikleri, ImageDataGenerator kullanılarak uygulanır. Eğitim verilerini çeşitlendirmek ve aşırı öğrenmeyi (overfitting) önlemek için rastgele kaydırma, yakınlaştırma ve kaydırma işlemleri yapılır. Test seti için yalnızca normalizasyon uygulanır.

### 3. Model Kurulumu

Model, Keras Sequential API kullanılarak oluşturulmuştur. Mimaride:

- Flatten Layer: 2D görüntü dizisini 1D vektöre dönüştürür.
- Dense Layers: ReLU aktivasyonlu tam bağlantılı katmanlar ve aşırı öğrenmeyi önlemek için L2 düzenleme içerir.
- BatchNormalization ve Dropout: Öğrenme sürecini stabilize etmek ve düzenlemek için kullanılır.
- Çıkış Katmanı: 9 birimli softmax katmanı, her bir balık türünü temsil eder.

### 4. Model Eğitimi

Model, Adam optimizasyonu ve kategorik çapraz entropi kaybı fonksiyonu ile derlenmiştir. ReduceLROnPlateau, doğrulama kaybında duraklama gözlemlendiğinde öğrenme hızını azaltmak için kullanılır. EarlyStopping ise iyileşme gözlenmezse eğitimi erken durdurur.

### 5. Model Değerlendirmesi

Modelin performansı, test seti üzerinde doğruluk ve kayıp ölçütleriyle değerlendirilir. Ayrıca, modelin her sınıf için performansını görselleştirmek amacıyla karışıklık matrisi oluşturulur.


