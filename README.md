Makine Öğrenmesi Projesi: Veri Kazıma ve Model Uygulama

Bu proje, makine öğrenmesi algoritmaları kullanılarak veri kazıma (web scraping) yoluyla elde edilen verilerin işlenmesini, analiz edilmesini ve modellerle sınıflandırılmasını veya tahmin edilmesini amaçlamaktadır. Proje boyunca veri işleme adımları, makine öğrenmesi modellerinin kurulması ve optimizasyonu gibi birçok konu ele alınmış, elde edilen sonuçlar yorumlanmıştır.

Proje Adımları

1. Veri Kazıma (Web Scraping)
Projede ilk olarak, veriler Trendyol'un "kadın çanta" kategorisinden kazınmıştır. Bu kategori, ürün başlıkları, fiyatları, puanları ve diğer bilgiler açısından zengin bir veri kaynağı sunmaktadır.

•	Veri Kaynağının Seçimi: Trendyol, çok sayıda ürünü ve detaylı bilgileri ile analiz için uygun bir platformdur.

•	HTML Yapısının Analizi: Site öncelikle HTML etiketleri incelenerek, gerekli bilgilerin hangi alanlarda yer aldığı belirlenmiştir.

•	Veri Kazıma Araçları: requests kütüphanesi ile HTTP istekleri yapılmış, gelen yanıtlar BeautifulSoup yardımıyla işlenmiştir. Ürünlerin başlık, fiyat ve puan gibi bilgileri toplanıp, CSV dosyasına kaydedilmiştir.

•Daha fazla veri elde etmek için sayfalama teknikleri kullanılarak, çok sayıda ürün verisi kazınmıştır.


2. Veri Temizleme ve Hazırlama
•Kazınan veriler, makine öğrenmesi modelleri için çalışabilir hale getirilmiştir.

•Eksik Veriler: Fiyat bilgisi olmayan satırlar kaldırılldı, puan veya yorum sayısı gibi eksik bilgiler sıfırla dolduruldu.

•	Veri Formatının Düzenlenmesi: Fiyatlar gibi metinsel formatta gelen veriler, sayısal formata dönüştürülmüştür.Marka string değerleri LabelEncoder() kullanarak de sayısal hale getirildi.

•	Aykırı Değerlerin Temizlenmesi: Fiyatlar veya puanlar gibi alanlarda normalin dışında kalan veriler tespit edilmiş ve veri setinden kaldırılmıştır.

•	Normalizasyon: Veriler, modellerin daha dengeli öğrenebilmesi için normalize edilmiş (0-1 arasına çekilmiştir).


3. Makine Öğrenmesi Modelleri
Hazırlanan veri seti, farklı makine öğrenmesi modelleri ile analiz edilmiştir. Kullanılan modeller ve öne çıkan özellikleri şunlardır:
 
	 Random Forest Regressor
•	Birden fazla karar ağacının birleştirilmesi ile tahminlerde daha doğru ve dengeli sonuçlar vermektedir.
•	Aşırı öğrenme (overfitting) riskini azaltmak için rastgele örnekleme ve özellik seçimi tekniklerini kullanır.

    Gradient Boosting Regressor
•	Bir dizi modeli ardışık olarak oluşturur ve her model, bir önceki modelin hatalarını öğrenerek daha doğru tahminler yapar.

    K-Nearest Neighbors (KNN - Regresyon)
•	Veri noktasının en yakın komşularına bakarak tahmin yapar. Ancak, büyük veri setlerinde veya yüksek boyutlu verilerde performans kaybı yaşar.

    Random Forest Classifier
•	Karar ağaçlarını birleştirerek sınıflandırma problemlerinde doğruluğu artırır ve karmaşık veri yapılarında etkili sonuçlar sağlar.


4. Optimizasyon (Hiperparametre Ayarlama)

Modellerin performansını iyileştirmek için Optuna kütüphanesi kullanılmıştır. Bu kütüphane, hiperparametrelerin en verimli şekilde seçilmesine yardımcı olur. Bu sayede, her modelin tahmin başarısı artmış ve daha doğru sonuçlar elde edilmiştir.


5. Sonuçlar

Bu projede, farklı makine öğrenmesi modellerinin performansları, regresyon ve sınıflandırma problemleri için analiz edilmiştir. Modeller aşağıdaki metrikler kullanılarak değerlendirilmiştir:

MAE (Ortalama Mutlak Hata): Tahminlerin gerçek değerlere olan ortalama mutlak sapmasını ifade eder. Daha düşük değer, daha iyi performans anlamına gelir.

MSE (Ortalama Kare Hata): Büyük hatalara daha fazla ağırlık veren bir metriktir. Düşük MSE, modelin daha doğru olduğunu gösterir.

R² (Determinasyon Katsayısı): Modelin veri setindeki değişkenliği ne kadar iyi açıkladığını gösterir. Değeri 1'e ne kadar yakınsa model o kadar başarılıdır.

MAPE (Ortalama Yüzde Hata): Modelin tahminlerinin, gerçek değerlere göre yüzdelik sapma oranıdır. Daha düşük MAPE, daha doğru bir model anlamına gelir.


Regresyon Modelleri:

Random Forest Regressor:
En düşük MAE ve MSE değerleri ile en iyi performansı göstermiştir. R² değeri (%89.9) ile veri setini en iyi şekilde açıklamıştır.

MAPE oranı da (%19.40) diğer regresyon modellerine göre oldukça düşüktür.

Sonuç: Regresyon problemleri için en başarılı modeldir.


Gradient Boosting Regressor:
Random Forest modeline kıyasla biraz daha yüksek hata oranlarına sahiptir. Ancak MSE ve R² açısından tatmin edici sonuçlar sunmuştur.

KNN:
Tüm regresyon modelleri arasında en düşük performansı göstermiştir. Özellikle MAPE oranının (%99.79) yüksek olması, modelin tahminlerde tutarsız olduğunu göstermektedir.


Sınıflandırma Modelleri:

Random Forest Classifier:
Düşük MAE (%0.23) ve MAPE (%13.92) değerleri ile sınıflandırma problemleri için en iyi performansı göstermiştir.
R² değeri (%83.0) sınıflandırma problemleri için oldukça iyidir.

En İyi Modeller:

Regresyon Problemi:

Random Forest Regressor, en yüksek R² (%89.9) ve en düşük hata oranları ile açık ara en başarılı modeldir.

Sınıflandırma Problemi:

Random Forest Classifier, düşük MAPE (%13.92) ve MAE (%0.23) ile en iyi sınıflandırma modelidir.

Youtube:https://www.youtube.com/watch?v=fNW4o-oddM8

Python sertifikası:[Sıfırdan_İleri_Seviye_Python_Programlama_Sertifika.pdf](https://github.com/user-attachments/files/18468400/Sifirdan_Ileri_Seviye_Python_Programlama_Sertifika.pdf)





Ad:Çiğdem Avcı

Numara:20360858035

Bursa Teknik Universitesi/Bilgisayar Müheendisligi/Makina Ogrenmesi Dersi





