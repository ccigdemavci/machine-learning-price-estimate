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
•Kazınan veriler, makine öğrenmesi modelleri ile çalışabilir hale getirilmiştir.

•Eksik Veriler: Fiyat, puan veya ürün açıklaması gibi eksik bilgiler ya ortalama ile doldurulmuş ya da ilgili veriler setten çıkarılmıştır.

•	Veri Formatının Düzenlenmesi: Fiyatlar gibi metinsel formatta gelen veriler, sayısal formata dönüştürülmüştür. Kategorik veriler sayısal kodlara (örneğin, "one-hot encoding") dönüştürülmüştür.

•	Aykırı Değerlerin Temizlenmesi: Fiyatlar veya puanlar gibi alanlarda normalin dışında kalan veriler tespit edilmiş ve veri setinden kaldırılmıştır.

•	Normalizasyon: Veriler, modellerin daha dengeli öğrenebilmesi için normalize edilmiş (0-1 arasına çekilmiştir).


4. Makine Öğrenmesi Modelleri
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


3. Optimizasyon (Hiperparametre Ayarlama)

Modellerin performansını iyileştirmek için Optuna kütüphanesi kullanılmıştır. Bu kütüphane, hiperparametrelerin en verimli şekilde seçilmesine yardımcı olur. Bu sayede, her modelin tahmin başarısı artmış ve daha doğru sonuçlar elde edilmiştir.


5. Sonuçlar

Farklı modeller, aşağıdaki performans metrikleri ile karşılaştırılmıştır:

•	MAE (Ortalama Mutlak Hata): Tahminlerin gerçek değerlere ortalama sapması.

•	MSE (Ortalama Kare Hata): Hataların kareleri alınarak hesaplanan ortalama.

•	R² (Determinasyon Katsayısı): Modelin veri setini açıklama oranı.

•	MAPE (Ortalama Yüzde Hata): Gerçek değerlere oranla ortalama yüzde hata oranı.

En İyi Modeller

 Regresyon Problemi: Random Forest, en düşük hata oranları ve en yüksek R² (%89.9) ile en başarılı modeldir.

 Sınıflandırma Problemi: Random Forest Classifier, düşük MAPE (%13.92) ve MAE (%0.23) değerleriyle sınıflandırma problemlerinde en iyi sonucu vermiştir.

Bu proje, farklı makine öğrenmesi modellerinin regresyon ve sınıflandırma problemlerinde nasıl performans gösterdiğini ortaya koymuş, veri işleme ve analiz süreçlerinin önemini gözler önüne sermiştir.

Youtube:

Python sertifikası:[Sıfırdan_İleri_Seviye_Python_Programlama_Sertifika.pdf](https://github.com/user-attachments/files/18468400/Sifirdan_Ileri_Seviye_Python_Programlama_Sertifika.pdf)






